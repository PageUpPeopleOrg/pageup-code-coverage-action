# pageup-code-coverage-action
PageUp .Net code coverage action

Add this action for you PR's to enable code coverage reporting.
To ensure only your code assemblies are included in code coverage and not inlude test suites or nuget packages, perform the following:

In visual studio set the company to "PageUp" under project properties -> Package -> General -> Company field for each of the projects you want included in code coverage analysis
