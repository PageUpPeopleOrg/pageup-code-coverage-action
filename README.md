# pageup-code-coverage-action
PageUp .Net code coverage action

Add this action for you PR's to enable code coverage reporting.

## How to setup 

By default, when running code coverage, all assemblies touched by the test are included in code coverage reporting.
This is not ideal since it means 3rd party NUGET packages, as well as your tests assemblies get included in coverage which throws out the calculation and adds noise.
Therefore, rather than trying to manage along and complicated list of exclusions whichmay vary by project, we have option for configuring what to include in coverage.

To ensure only your code assemblies are included in code coverage and not inlude test suites or nuget packages, perform the following:

In visual studio set the Company property to "PageUp" under each projects properties you whish to include 
 - Project settings ->  Package -> General -> "Company" 
