---
title: "Code smells and the lessons I learned"
category: Software
date: 2020-12-04 15:41:00 -0300
comments: true
description: Code is a craft that takes patience and practice to master. This particular collection of thoughts may help you identify bad practices that cause you problems and guide your team towards a better planning and change decisions in your product.
---

<img src="/images/posts/2020-12-04-Code_smells_and_the_lessons_I_learned/668634e6-b874-4199-8bbb-328911922a85.jpg" alt="Code smells"/>

Code is a craft that takes patience and practice to master. Throughout the years I have worked in all sorts of projects, using all kinds of methodologies and with people from different places and I realised that there were some patterns in my or my teammate’s code that stand it out and caused a lot of trouble later on.

These code blocks often would haunt us and rig the project, making progress more and more difficult to the point that simple changes would require lots of energy makes us tremble with fear to execute it.

With time, It became easier to identify certain bad decisions or **code smells** and fix it or stir to the right direction before it becoming a problem for us.

Nonetheless I started to collect some thoughts and conventions here and there and starting to apply on daily basis. This particular collection of thoughts may help you identify bad practices that cause you problems and guide your team towards a better planning and change decisions in your product.

If you are really interested in this subject, I can’t recommend enough the works of Robert C. Martin, in particular the book [Clean Code](https://www.oreilly.com/library/view/clean-code-a/9780136083238/). It is a marvellous account of Martin’s experience filled with good advices on building a consistent, reliable and maintainable product.

As I found out, most of the tips that I gathered from experience on the field are the ones discussed in his book.

Back to our collection of bad smells, I divided into different categories in order to serve you as a checklist:

1. Environment
2. Writing functions and classes
3. Tests
4. Comments and documentation

Without further ado, here we go:

# Environment smells

## 1. Build your project takes more than one step

Setting up a project should be as easy as it gets. If your project needs more than one command to start, or a multitude of configurations prior start, you should revise this process to see what can be done to make it easier.

## 2. Execute your tests takes more than one step

Your test base should be as smooth and simple as possible. This is important because reduces the friction of this step in the development procedure. This ensure a nice start for your devs as well a secure release. I have prepared a section exclusively to talk about tests because I believe that this is one of the most important steps you can take to improve your code skills and the overall quality of your project.

# Writing functions and classes

In this section I would like to point out few tips about the quality of a function. There are much more we can talk about but the following 4 points are essential patterns to identify and get rid of it for good:

## 1. Too many arguments

Following the Single-responsibility principle [1](https://en.wikipedia.org/wiki/Single-responsibility_principle), our functions should be have responsibility over one single part of the program. Basically it states that a function must do only one thing and do it well. When a function takes too many arguments or a class has too many functionalities, this is a hint that it should be broken up. As a rule of thumb I try to keep my function with 3 arguments max. This way your software becomes easier to write, comprehend, test and scale.

## 2. Avoid change argument by reference

A function that modifies its arguments instead of returning a result is counterintuitive and can bring a lot of confusion when implementing it. If the purpose of your function is receive an argument and return something based on this same argument (like a map, reduce or sort) you should return it instead of modifying the argument variable itself.

## 3. Avoid adding “flag” arguments to your function

Flag arguments are a Boolean variables passed to a function in order to make it behave in a certain way. Following the principle we stated above we should keep our functions simple and focused as a laser on a single part of our software. If you feel the urge to add a flag that’s a sign you should break this function or check the function’s caller requirements.

## 4. Dead functions

As our software grows we grow with it, finding new solutions and extending it with new functionalities. As a tree grows over time, it is only natural that some leafs will dry and fall. When this time comes it is our responsibility to take care of this tree by cleaning up and nurturing it to grow even taller. As with our software, as we change it we should keep an eye on functions that have no use anymore and remove it.

# Tests

Writing tests is an art. As several authors, developers and engineers have stated before, written tests are too much helpful tool to let it go to waste, so we should always try to write it and write it well.

We must be as careful with our tests as we are with our code and likewise there are some tips that will help us to avoid a mess.

## 1. Insufficient tests

A test suite should test everything that could possibly break. The tests are insufficient so long as there are conditions that have not been explored by the tests or calculations that have not been validated.

## 2. Use a coverage tool

We can only improve what can be measured. And a coverage tool will help us understand where the clinks in the armour are. Possibly you will never get 100% coverage, but this will lay a map that will guide you towards the most critical parts of your project. Then it is only a Paretto’s principle [2].

## 3. Don’t skip trivial tests

You know feeling that the small changes you made won’t cause any harm so to speed up things you publish without testing? Well, often times it results in problems. Test everything you do and don’t you ever underestimate changes no matter its size.

## 4. An ignored test is a question about an ambiguity

Avoid commenting tests for “latter use” or tagging them as `ignored` or `skip`. It is importante to keep the test suite as clear and objective as possible to avoid confusion by other developers or yourself later.

## 5. Test boundary conditions

Boundary conditions are these cases that almost satisfy the condition but not, ie, are at the threshold of your case. Often times when working with numbers these boundary cases are more prominent, and as a rule of thumb always take a look at conditions inside the function you are testing.

Take special care to test boundary conditions. We often get the middle of an algorithm right but misjudge the boundaries. In principle, all possible cases of all conditions in the function should have a test to assert it.

## 6. Exhaustively test near bugs

Bugs tend to congregate. When you find a bug in a function, it is wise to do an exhaustive test of that function. You’ll probably find that the bug was not alone.

## 7. Patterns of failure are revealing

Sometimes you can diagnose a problem by finding patterns in the way the test cases fail. As Robert C. Martin says:

> As a simple example, suppose you noticed that all tests with an input larger than five characters failed? Or what if any test that passed a negative number into the second argument of a function failed?

## 8. Tests should be fast

Your test should be simple, clear and objective. Avoid using procedures that delay the test like `delay()`, `setTimeout`, etc. The full test suit will often have thousands os test cases so every millisecond counts.

# Comments

Commenting your code is another topic that adds a lot of value to your code. It is the space you have to add your rationale behind the written code or intricate logic when design is not enough. Writing a good comment helps your peers to understand your decisions and passes on the knowledge. But you should be aware to add just the necessary and take precautions to not add confusion instead of clarity in the project.

Along the way I found out these tips that helped me and my teammates to prevent confusion and truly add value to the project:

## 1. Inappropriate information

Comments should be reserved for technical notes about code and design. Refrain yourself to write unrelated information or information that should be better handled by a software such as:

- Add author name or last update in the head of the file. That is the job of your versioning system;
- List of fixes as a TODO list. You can add a unique id to relate a certain task of RFC, but avoid add extensive list of changes as if the file were a Kanban board;
- Change history. Like the autor’s name, this should be handled by your versioning system instead of kept manually by your team.

## 2. Obsolete comments

Every time you make a change in a part of the code, be sure that the comments around reflect your intention. Avoid keeping old comments to prevent confusion further on.

## 3. Redundant comments

You should pay attention to the extra information is not redundant or repetitive. The golden rule here is that your code should be simple and clear enough for everyone to understand.

You should be able to add your intent into the code you write and if this is not enough, you may add new information to explain your rationale.

For example, lets say your has a series of conditions to solve:

```python
# Value is smaller than value and greater than max
if (min < value and value < max):
  return 'Value is between min and max'

# Value is smaller than min
if (min > value):
  return 'Value is smaller than min'

# Value is greater than max
if (max < value):
	return 'Value is greater than max'
```

As it is, you do not need any comment to explain what is happening because is pretty straightforward. This part is totally optional but you could create a variable to hold the condition’s results, aggregating more value and intention to your code:

```python
isBetweenMinAndMax = min < value and value < max
isSmallerThanMin = min > value
isGreaterThanMax = max < value

if (isBetweenMinAndMax):
  return 'Value is between min and max'

if (isSmallerThanMin):
  return 'Value is smaller than min'

if (isBetweenMinAndMax):
	return 'Value is greater than max'
```

For the given example you do not need to do this, but for complex conditions that end up involving several variables, it is a nice touch to attribute the result to a more readable variable.

## 4. Bad written comments

Worst than no comments are bad written comments. If you are taking the time to explain the rationale behind your logic, you should be careful what you write is making sense. Double check your comments before moving on to the next change.

## 5. Commented out code

This is a good one. One should always refrain to comment out code thinking “shall be useful later”. To avoid confusion in the project, just delete the code parts you do not need and let your versioning system (git, svn, etc.) take care of the changes history. Wherever you need the deleted code, you can always go back and recover it.

# Conclusion

We covered a lot of terrain today and I hope these tips may guide you as much as it has guided me in developing high-quality software. But the journey is not done yet, I still have some general tips to share with you about all different corners of your project.

But let’s talk about them another day. For now take a deep breath and reflect a little about the tips we discussed, what you liked and disliked; and what work or not work for you.

See you next time!

# References

1. Wikipedia. _Single-responsibility principle - Wikipedia_. Available in: https://en.wikipedia.org/wiki/Single-responsibility_principle. Accessed in: 3 Dec 2020
2. Wikipedia. _Pareto principle_. Available in: https://en.wikipedia.org/wiki/Pareto_principle. Accessed in: 3 Dec 2020
