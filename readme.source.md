# <img src="/src/icon.png" height="30px"> Xunit.ApprovalTests

[![Build status](https://ci.appveyor.com/api/projects/status/5x0gasnuhtblvcv2/branch/master?svg=true)](https://ci.appveyor.com/project/SimonCropp/Xunit.ApprovalTests)
[![NuGet Status](https://img.shields.io/nuget/v/Xunit.ApprovalTests.svg?cacheSeconds=86400)](https://www.nuget.org/packages/Xunit.ApprovalTests/)


The default behavior of ApprovalTests uses the [StackTrace](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.stacktrace) to derive the current test and hence compute the name of the approval file. This has several drawbacks/issues:

 * Fragility: Deriving the test name from a stack trace is dependent on several things to be configured correctly. Optimization must be disabled to avoid in-lining and debug symbols enabled and parsable.
 * Performance impact: Computing a stack trace is a relatively expensive operation. Disabling optimization also impacts performance

Xunit.ApprovalTests avoids these problems by using the current xUnit context to derive the approval file name.


toc


## NuGet package

https://nuget.org/packages/Xunit.ApprovalTests/


## Usage

Usage is done via inheriting from a base class `XunitApprovalBase`

snippet: XunitApprovalBaseUsage


## xUnit Theory

[xUnit Theories](https://xunit.net/docs/getting-started/netfx/visual-studio#write-first-theory) are supported.

snippet: Theory

Will result in the following `.approved.` files:

 * `Sample.Theory_value=Foo.approved.txt`
 * `Sample.Theory_value=9.approved.txt`
 * `Sample.Theory_value=True.approved.txt`


## AsEnvironmentSpecificTest

ApprovalTests `NamerFactory.AsEnvironmentSpecificTest` is supported.

snippet: AsEnvironmentSpecificTest

Will result in the following `.approved.` file:

 * `Sample.AsEnvironmentSpecificTest_Foo.approved.txt`


## UseApprovalSubdirectory

ApprovalTests `[UseApprovalSubdirectory]` is supported.

snippet: UseApprovalSubdirectory

Will result in the following `.approved.` file:

 * `SubDir\Sample.InSubDir.approved.txt`


## ForScenario

ApprovalTests `ApprovalResults.ForScenario` is supported.

snippet: ForScenario

Will result in the following `.approved.` file:

 * `Sample.ForScenarioTest_ForScenario.Name.approved.txt`


## Base Class

When creating a custom base class for other tests, it is necessary to pass through the source file path to `XunitApprovalBase` via the constructor.

snippet: XunitApprovalCustomBase


## Release Notes

See [closed milestones](../../milestones?state=closed).


## Icon

[Wolverine](https://thenounproject.com/term/wolverine/18415/) designed by [Mike Rowe](https://thenounproject.com/itsmikerowe/) from [The Noun Project](https://thenounproject.com/).