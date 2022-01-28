# Costa
Repository
name: JS Tests

on:
  push:
    branches-ignore:
      - "dependabot/**"
  pull_request:
  workflow_dispatch:

env:
  FORCE_COLOR: 2
  NODE: 16

jobs:
  run:
    name: JS Tests
    runs-on: ubuntu-latest

    steps:
      - name: Clone repository
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: ${{ env.NODE }}
          cache: npm

      - name: Install npm dependencies
        run: npm ci

      - name: Run dist
        run: npm run js

      - name: Run JS tests
        run: npm run js-test

      - name: Run Coveralls
        uses: coverallsapp/github-action@1.1.3
        with:
          github-token: "${{ secrets.GITHUB_TOKEN }}"
          path-to-lcov: "./js/coverage/lcov.info"
