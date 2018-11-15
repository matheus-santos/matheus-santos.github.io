---
layout: default
title: "7 Best practices to follow when writing tests"
categories: code
comments: true
---

Hey folks, Matt here.

Today we are going to talk about a precious piece of our coding process: the unit tests. Basically a unit test is a method that tests a piece of code in order to determine if that piece is fit for use. Can involve different modules, operating and usage procedures and control data and its role is to ensure that the execution flow goes as expected.

Adding this process to your workflow will skyrocket the quality of your code by several reasons, among them:

- Make your code easier to refactor since the method outcomes are pre-defined;
- Force you to think with a modular mindset to make them easier to assert;
- You can automate the running process to alert when something is off;
- Forces you to think about all possible outcomes and side effects that your code might have on the project;
- Helps your colleagues to understand what is going on in your code when you are not around;
- Ensures that the code you are shipping works as it should be. Think like a quality seal;

## Basic topics and how to structure your test

But before diving into the best practices we are going to talk about how to structure the test set.

### Integration and Unit tests

This is a very strong principle that helps us to see our project in two perspectives being the first a detailed one by creating test cases that assert a small piece of our software like a function or a class; and the second one the interaction among these small pieces and how they work together in an integrated environment.

An unit test is a test case where you focus on a single output of a single method in your software. If your sofware have a simple `if` inside it you will have to cover at least two cases in order to guarantee that your method works as intended:

```python
function helloUser(name):
    return name
        ? 'Hello ' + name # Test one: call function passing name
        : 'Hello stranger' # Test two: call function passing nothing
```

In the example above, we have either the message "Hello stranger" when `name` is empty and "Hello Matt" when `name` is provided.

As a rule of thumb you should write unit tests for each possible output in your method, reducing the need to rewrite theses cases again when you apply this method throughout your software. Save the integration tests to complex interactions like whole user stories.

An integration test is when you have process that need to be tested end-to-end and involves different methods, classes and even modules. Take for example an checkout process in a e-commerce we have roughly these steps:

1. User login or register
2. Calculate items in cart
3. Charge user

To create a complete integration test would take lots of different variables to take account into, so the rule of thumb is to keep integration tests to core activities in your system. It is very important to write these up because the isolation principle of the unit tests do not guarantee that the whole will work. We can experience lots of unpleasant surprises when connecting these dots for all sorts of reasons: bad design, lack of communication, different API and so on.

The tip here is to think about scope: isolate methods to its most atomic functioning makes easier to predict its behaviour when combining them to create more complex pieces.

### Test-Driven Design principle

As we discussed above, write every possible output for your function has become a well praised and welcome habit. The Test-Driven Design (TDD) forces us to think first on the cases to test before writing the method itself. This approach helps us think about the complexity we are about to introduce. It is very common to get into questions like "Does this function should do this?", "Does this function really needs this piece of information?" and maybe the most important "Do this function have should have so many outputs?".

When thinking in TDD, the most important takeout is to spot methods that do more they should therefore must be split into smaller pieces, making our life easier.

This changes our mindset towards a more atomic writing and understable interpretation about what we are doing.

### Coverage and objectivity

Sometimes we take these tests to serious and start to testing things we should not or even duplicating cases. It is important to differ what your test is covering before add to the test base.

Basically, your tests should cover your business logic. Applying unit tests and few integration tests may help to keep a concise base and prevent dumb or redundant tests. Remember that you don't need to test your dependencies, just the integration with then and even so you can apply a mock just to prevent calling unecessary third-parties.

As the time goes, your test base tends to become bigger than your own software, so this principle is very important. We don't want to slow down our QA process because the tests are taking to long, so keep it DRY (don't repeat yourself).

### AAA principle

This one is what leverage the way that I write tests to another level. The AAA principle tells us to divide our test case into three blocks: Arrange, Act and Assert. This makes the method easier to understand and maintain and really helps when you have to refactor some tests or clean up your base. So when building your code, remember to structure your test case as the following:

- **Arrange** your code by preparing all data required to test this case;
- **Act** only on the function you intend to test. Remember that you are testing only one case of one function, so keep the focus;
- **Assert** the result by comparing with expected results

## Checklist with best practices for your unit tests

Ok, we talked a lot about the basics so I will just dive in the checklist that helps us to guarantee an effective and understable test collection of our software. So here we go

1. **Follow the AAA principle**

Arrange, Act and Assert. That is the drill. Following this tip will help you clearly communicate your intentions with a given test case.

2. **Your asserts should be concise and minimal for each method**

Stick to TDD and you can't go wrong. Write small pieces of software with few outputs will help you to predict behaviour and therefore reduce problems.

3. **The asserts must have a clear description**

ALWAYS write your intentions with a test case. Maybe in a few months you will have to go back and revise it. Be nice to your future self.

4. **The code must be clear and easy to understand**

Again TDD is an effective approach to ensure this. Fewer outputs means fewer cases therefore each test cases tests only one thing at a time.

5. **You must avoid test interdependence**

Isolate your methods is another effective tip to prevent surprises. Each test case must work for itself. In other words your test case must be self sufficient and provide all the information it needs to run alone and of course, prevent to interfere with results of other tests.

6. **Group your tests using tags or method name standards**

This is more a tip that helps me to maintain a test collection. To speed things up you can run only grouped tests as your progress with your software, making the work in progress faster.

7. **Your tests should be easy to execute**

We should be able run any test anytime with little to no need to prepare it. If our test cases are really self sufficient then we are able to run it easily and painlessly.

## Conclusion

That's it, today we talked about some suggestions that helped me along the way and can be useful for you too. The main takeaway here is to consider the TDD approach whatever possible. Maybe your project doesn't really need it or your are already using a different methodology like Behaviour-Driven Development (BDD) or Domain-Driven Development.

The important part here is to think in modules or small blocks that will be used to build up something bigger. If any small block is bad the whole tower can crumble so make sure each little brick is solid as intended to.
