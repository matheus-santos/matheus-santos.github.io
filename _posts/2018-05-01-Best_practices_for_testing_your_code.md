---
layout: default
title:  "Best practices for testing your code"
date: 2018-05-1 20:27:00 -0300
categories: test code tutorial
comments: true
---

## Advices about unit tests and why is important

Hey folks,

Today we are going to talk about a precious piece of our coding process: the unit tests. Basically a unit test is a method that tests a piece of code in order to determine if that piece is fit for use. Can involve different modules, operating and usage procedures and control data and its role is to ensure that the execution flow goes as expected.

Adding this process to your workflow will skyrocket the quality of your code by several reasons, among them:

- Make your code easier to refactor since the method outcomes are pre-defined;
- Force you to think with a modular mindset to make them easier to assert;
- You can automate the running process to alert when something is off;
- Forces you to think about all possible outcomes and side effects that your code might have on the project;
- Helps your colleagues to understand what is going on in your code when you are not around;
- Ensures that the code you are shipping works as it should be. Think like a quality seal;

But before diving into the best practices list we are going to talk about how to structure the test set and some other principles.

// Integrations vs Unit
// TDD
// Remember that quantity is not equal to quality
// Simple unit test
// Anatomy of a unit test
 
## Best practices for your unit tests

1. Follow the AAA principle
2. Your asserts should be concise and minimal for each method
3. The asserts must have a clear description
4. The code must be clear and easy to understand
5. You must avoid test interdependence
6. Group your tests using tags or method name standards
7. Your tests should be easy to execute

## Next step: integration

## References

1. [Toptal - How to write testable code and why it matters](https://www.toptal.com/qa/how-to-write-testable-code-and-why-it-matters)