# Costa
Repository

Pravin Kumar
UI/UX Designer • Graphic Designer • Digital Marketing
Chandigarh, India Contact info

    500+ connections

AboutAbout

Hi, I'm Pravin and I'm currently in my last year studying Bachelor's in Business Administration. I've been lucky 
to have got some time to explore many fields of study; having these experiences has enriched my practice as a 
designer. Design work is always exciting to me because I'm constantly learning new things and challenging my 
own perspectives.


EducationEducation

    Amity University logo
    Amity UniversityAmity University
    Bachelor's degree, Business Administration and ManagementBachelor's degree, Business Administration and Management 2019 - 20222019 - 2022
    Birla international schoolBirla international school
    ScienceScience 2017 - May 2019
    
    
Skills

    User Experience Design (UED)User Experience Design (UED) · 2· 2
    Human Resources (HR)Human Resources (HR) · 2· 2
    Graphic DesignGraphic Design · 2
    
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
        name: CSS

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
  css:
    runs-on: ubuntu-latest

    steps:
      - name: Clone repository
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: "${{ env.NODE }}"
          cache: npm

      - name: Install npm dependencies
        run: npm ci

      - name: Build CSS
        run: npm run css

      - name: Run JS tests
        run: npm run js-test

      - name: Run Coveralls
        uses: coverallsapp/github-action@1.1.3
        with:
          github-token: "${{ secrets.GITHUB_TOKEN }}"
          path-to-lcov: "./js/coverage/lcov.info"
