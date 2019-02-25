---
layout: post
title: Test Driven Development One Month Check-in
---
### Intro
I have been trying TDD for about a month now, and I wanted to take time to reflect on my experience on TDD to think about what worked what didn’t and to find a room for improvements to be better at TDD. 

(My TDD practice knowledge comes from *Test-Driven Development: A Practical Guide by David Astels*. While I was writing this post, I read through *Test Driven Development: what it is, and what it is not by Andrea Koutifaris* to remind myself of TDD practice and compare with the way I am doing it).

### How it should be done
*Test Driven Development: what it is, and what it is not by Andrea Koutifaris* does a great job in summarizing what TDD and how it needs to be done. (This is very much in line with what I read from *Test-Driven Development: A Practical Guide by David Astels*) TL;DR Programming in TDD model consists of three steps. 1. Write test that fails. 2. Write code to make the test pass 3. Refactor. 

1. Write test that fails. 
This needs to happen before any code. In many cases, test will use a class or functions that doesn’t exist yet, which causes compile error. This is okay. One of the goals of this phase is to come up with an intuitive apis for user’s perspective for the classes and functions to be implemented. So, it actually makes more sense to write test first before thinking about all the implementation details of the apis. 

> It is in this phase where you concentrate on writing a clean interface for future users. This is the phase where you design how your code will be used by clients. 
>
> -- <cite>*Test Driven Development: what it is, and what it is not by Andrea Koutifaris*</cite>

2. Write code to make the test pass.
This phase should focus only on writing the code so that the test passes. One of the key things in this phase is to write as little code as possible to pass the test. 

> In this phase, you need to act like a programmer who has one simple task: write a straightforward solution that makes the test pass (and makes the alarming red on the test report becomes a friendly green). In this phase, you are allowed to violate best practices and even duplicate code. Code duplication will be removed in the refactor phase.
> 
> -- <cite>*Test Driven Development: what it is, and what it is not by Andrea Koutifaris*</cite>

3. Refactor
This is the time to refactor the code to be clean to remove duplicate code and to add abstraction layer. The beauty of TDD is that as long as all the tests pass, you know the refactor is safe. 

### How I am doing it 
Reflecting back, it seems like I am not following TDD in strict sense. Instead of breaking development into three steps, I am doing it in two steps. 1. Write test that fails 2. Write code to make the test pass. I think my Step 1 is similar to recommended Step 1 in that I write test before defining class or function signature. However, my Step 2 is a mix of Step 2 and 3 of strict TDD. While I write the code to make the test pass, I do refactoring to reduce duplicate code and sometimes add “unnecessary” functions to make the feature more complete. Another thing is that I don’t refactor test code so there are many duplicate code in tests. This is something that TDD books / guides tell not to do. 

### How I think about it so far
- I do think that writing the test first helps in writing clean and intuitive apis for class and functions since I am forced to think from user perspective first before I do a deep dive into implementation detail. 
- Similarly, it also helps in designing code so that it is easier to test. One thing that I noticed was that as I started doing TDD, my functions became much more focused. Instead of having a few functions that does a lot of things, TDD forces the code to write more small functions that does one thing well. It also prevents me to use global state which makes testing more difficult.  
- I am facing challenge when writing test for class or function that simply class other functions. The functions that get called under-the-hood are already tested, so testing the functionality of the parent function seems like a duplicate test. Alternative that I can think of is to mock the underlying functions. However, mocking all underlying functions can become tedious and also sometimes it feels like it leads to high coupling between test and the function’s implementation detail. 
- Writing actual test does not take much time after getting used to a testing framework. Majority of the time added due to TDD comes from thinking about what test to write. One of the reason why it takes long time to think is because I am not used to breaking a big feature into smaller building block features. For example, when I am working on a feature A, I can’t just start by writing a unit test that tests the feature A. Because in order to make that test pass, I need smaller building block feature, which will need tests for before implementing. Since TDD is one failing test a time, this approach won’t work. Instead, I need to break a feature A into smaller building block features which I can write test for without causing cascading needs for sub-features that need tests. 
- It’s okay not to follow TDD all the time. When I first started TDD I tried to follow TDD for every single thing. I was afraid that if I don’t follow TDD all the time I will move out of it. However, this is bad practice. When an idea is in early stage that needs validation, it is worth doing fast prototyping to come up with a proof-of-concept to see if the idea makes sense first. There is no use of TDD to make the most beautiful code when the idea doesn’t work out at the end. 
- External calls / apis need to be mocked for test. If those apis are not easy to mock, wrap them in a wrapper class that is easy to mock. 

### What to improve 
Based on these reflections, I think I need to improve on...
- For writing test phase, I need to focus more as a user of the apis. When I write tests, my brain switch back and forth between apis and implementation detail. This seems to delay the process of writing test without clear value from it. Maybe coming up with better design plan to know what classes I am going to write and how they are going to interact with each other will help in focusing just on apis during this process. 
- I need to improve on breaking down a feature (or project) into smaller building block features that I can easily apply TDD. I am not too clear how to improve this other than just keep practicing TDD, though. 
- I need to separate the step for writing code to make a test pass and refactoring. Because I do refactoring or write some additional code in the phase that I need to make the test pass, some features or functions can be left in a partially tested phase. 
  - This goes against 
    - > Here comes another mistake: do not write a bunch of functions/classes that you think you may need. Concentrate on the feature you are implementing and on what is really needed. Writing something the feature doesn’t require is over-engineering. 
      >
      > -- <cite>*Test Driven Development: what it is, and what it is not by Andrea Koutifaris*</cite>
- I need to figure out how to test classes / functions that simply calls other functions under-the-hood. I should probably look for examples of this case written by other people following TDD. 

Thanks for reading and please let me know if you have any feedback on my TDD approaches and understanding. 

