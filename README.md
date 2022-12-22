# pageup-code-coverage-action
PageUp .Net code coverage action

Add this action for you PR's to enable code coverage reporting.

## How to setup 


### Github workflow setup

Use the the below workflow template to configure concoverage reporting for your repo.
- Depending on the current test coverage level, you may want to shift up or down the **percentLowRange**  / **percentHighRange** range for the coverage reporting to incrementally move the dial upward on coverage
- using **failBuild** You can optionally configure thebuidl to failif you drop


`
name: CI
on:
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest
    if: github.event.pull_request.draft == false

    steps:
      - name: 🛒 Checkout code
        uses: actions/checkout@v3

      - name: 🔐 PageUp Code Scanning Action
        uses: PageUpPeopleOrg/pageup-codescanning-action@main      
        if: always()
      - name: 📈 PageUp Code Coverage report
        uses: PageUpPeopleOrg/pageup-code-coverage-action@main      
        if: always()
        with:
          failBuild: 'false'
          percentLowRange: '50'
          percentHighRange: '80'
`

### .Net solution setup

By default, when running code coverage, all assemblies touched by the test are included in code coverage reporting.
This is not ideal since it means 3rd party NUGET packages, as well as your tests assemblies get included in coverage which throws out the calculation and adds noise.
Therefore, rather than trying to manage along and complicated list of exclusions whichmay vary by project, we have option for configuring what to include in coverage.

To ensure only your code assemblies are included in code coverage and not inlude test suites or nuget packages, perform the following:

In visual studio set the Company property to "PageUp" under each projects properties you whish to include 
 - Project settings ->  Package -> General -> "Company"  => set to "PageUp"
