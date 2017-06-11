## Why Bother with Test Discipline?

Your tests are your first and best line of defense against software defects. Your tests are more important
than linting & static analysis (which can only find a subclass of errors, not problems with your actual 
program logic). 

**Tests are as important as the implementation itself (all that matters is that the code 
meets the requirement — how it’s implemented doesn’t matter at all unless it’s implemented poorly)**.

## Things that testing can do for you
 
 * **Design aid**: Writing tests first gives you a clearer perspective on the ideal API design.
 * **Feature documentation** (for developers): Test descriptions enshrine in code every implemented 
   feature requirement.
 * **Test your developer understanding**: Does the developer understand the problem enough to articulate 
   in code all critical component requirements?
 * **Quality Assurance**: Manual QA is error prone. In my experience, it’s impossible for a developer to remember 
   all features that need testing after making a change to refactor, add new features, or remove features.
 * **Continuous Delivery Aid**: Automated QA affords the opportunity to automatically prevent broken builds from being
   deployed to production.

##The different types of test

The first thing you need to understand about different types of tests is that they all have a job to do. They play important 
roles in continuous delivery.

You should isolate unit tests, integration tests, and functional tests from each other so that you can easily 
run them separately during different phases of development.

* **Unit tests** ensure that individual components of the app work as expected. Assertions test the component API.
* **Integration tests** ensure that component collaborations work as expected. Assertions may test component API,
    UI, or side-effects (such as database I/O, logging, etc…)
* **Functional tests** ensure that the app works as expected from the user’s perspective. Assertions primarily 
    test the user interface.


## What are Unit tests?

Unit tests exist to test individual units of software functionality. A unit is a module, component, or function. 
They’re bits of the program that can work independently of the rest of the program. The presence of unit testing 
implies that the software is designed in a modular fashion. You may hear once in a while that there are ways to make 
software “more testable.”

If you find that it’s hard to write unit tests for your program without mocking lots of other things, that’s a sign
that your program is not modular enough. Revealing tight coupling (the opposite of modularity) is one of the many 
important roles that unit tests play in software creation.

> The more you break your problems down into simple, pure functions, the easier it will be to test your code without mocks.

Unit tests should be:

* Dead simple.
* Lightning fast.
* A good bug report.
   
### The Unit Test as a Bug Report

When a test fails, that test failure report is often your first and best clue about exactly what went wrong — the
secret to tracking down a root cause quickly is knowing where to start looking. That process is made much easier when 
you have a really clear bug report.

What’s in a good test failure bug report?

1. Which component is under test?
2. What is the expected output (expected behavior)?
3. What was the actual output (actual behavior)?
4. How is the behavior reproduced?

The first three questions should be visible in the failure report. The last question should be clear from
the test’s implementation.

> When a unit tests fails, the error message is your bug report.


## Integration Tests

Integration tests ensure that various units work together correctly. For example, a Node route handler might take
a logger as a dependency. An integration test might hit that route and test that the connection was properly logged.

Many integration tests test interactions with services, such as 3rd party APIs, and may need to hit the network in 
order to work. For this reason, integration tests should always be kept separate from unit tests, in order to keep
the unit tests running as quickly as they can.

## Functional Tests

Functional tests are automated tests which **ensure that your application does what it’s supposed to do from the 
point of view of the user**. Functional tests feed input to the user interface, and make assertions about the output
that ensure that the software responds the way it should.

Functional tests are sometimes called end-to-end tests because they test the entire application, and it’s hardware
and networking infrastructure, from the front end UI to the back end database systems. In that sense, functional 
tests are also a form of integration testing, ensuring that machines and component collaborations are working as
expected.

Functional tests typically have thorough tests for “happy paths” — ensuring the critical app capabilities, 
such as user logins, signups, purchase work flows, and all the critical user workflows all behave as expected.

Functional tests should be able to run in the cloud on services such as Sauce Labs, which typically use the 
WebDriver API via projects like Selenium.

They work by simulating actions the end user might take in order to accomplish their goals in your app. They can
click buttons, input text, wait for things to happen on the page, and make assertions by looking at the actual 
UI output.

#### Smoke Tests
After you deploy a new release to production, it’s important to find out right away whether or not it’s working as 
expected in the production environment. You don’t want your users to find the bugs before you do — it could chase
them away!

It’s important to maintain a suite of automated functional tests that act like smoke tests for your newly deployed 
releases. Test all the critical functionality in your app: The stuff that most users will encounter in a typical 
session.

Smoke tests are not the only use for functional tests, but in my opinion, they’re the most valuable.