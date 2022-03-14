**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report \#4 – Mutation Testing and Web app testing**

| Group \#: | 27         |
| --------- | ---------- |
| Michele   | Esercitato |
| Dylan     | Mah        |
| Faisal    | Hossain    |
| Cheyenne  | Goh        |

**Table of Contents**

1. [Introduction](#Introduction)
2. [Analysis of 10 Mutants of the Range class](#Analysis-of-10-Mutants-of-the-Range-class)
3. [Report all the statistics and the mutation score for each test class](#Report-all-the-statistics-and-the-mutation-score-for-each-test-class)
4. [Analysis drawn on the effectiveness of each of the test classes](#Analysis-drawn-on-the-effectiveness-of-each-of-the-test-classes)
5. [A discussion on the effect of equivalent mutants on mutation score accuracy](#A-discussion-on-the-effect-of-equivalent-mutants-on-mutation-score-accuracy)
6. [A discussion of what could have been done to improve the mutation score of the test suites](#A-discussion-of-what-could-have-been-done-to-improve-the-mutation-score-of-the-test-suites)
7. [Why do we need mutation testing? Advantages and disadvantages of mutation testing](#Why-do-we-need-mutation-testing?-Advantages-and-disadvantages-of-mutation-testing)
8. [Explain your SELENUIM test case design process](#Explain-your-SELENUIM-test-case-design-process)
9. [Explain the use of assertions and checkpoints](#Explain-the-use-of-assertions-and-checkpoints)
10. [how did you test each functionaity with different test data](#how-did-you-test-each-functionaity-with-different-test-data)
11. [Discuss advantages and disadvantages of Selenium vs. Sikulix](#Discuss-advantages-and-disadvantages-of-Selenium-vs.-Sikulix)
12. [How the team work/effort was divided and managed](#How-the-team-work/effort-was-divided-and-managed)
13. [Difficulties encountered, challenges overcome, and lessons learned](#Difficulties-encountered-challenges-overcome-and-lessons-learned)
14. [Comments/feedback on the lab itself](#Comments/feedback-on-the-lab-itself)

# Introduction


# Analysis of 10 Mutants of the Range class


# Report all the statistics and the mutation score for each test class


# Analysis drawn on the effectiveness of each of the test classes
Some of the test classes were able to better find mutants than others. Comparing the original and new mutation scores, certain functions which reused local variables were better at killing mutants. However, most of the functions from the Range class and a few from the DataUtilities class were unable to kill the same type of mutants (ex. post-increment/decrement, condition changes). Due to this, our group needed to design extra test cases which were able to kill these mutants.

# A discussion on the effect of equivalent mutants on mutation score accuracy


# A discussion of what could have been done to improve the mutation score of the test suites


# Why do we need mutation testing? Advantages and disadvantages of mutation testing
Mutation testing allows for developers to see if the current program is able to catch more complex or rare errors. It also can help developers see if conditions for loops or if statements can be exploited. In general, mutation testing is another way to see how faults can be introduced by either the software or users.

The advantages of mutation testing include being able to find more faults, having more metrics to improve test suites and providing a more thorough check of the program's functionality.

The disadvantages of mutation testing include the amount of time and resources needed to implement it. Mutation testing takes a lot of time and a decent amount of computation power to automate, which slows down the development process.

# Explain your SELENUIM test case design process
Our group designed the Selenium test cases by first looking through the websites and seeing what functionality was available. Based on that, we would decide which paths to take in the website. Then, we would start Selenium and record our test cases. After this, we would replay them to check if Selenium was able to record all of the keystrokes and mouse clicks correctly.

# Explain the use of assertions and checkpoints
Our group used assertions to see if Selenium clicked the right part of the webpage and if the correct GUI element was available. This would help with error checking the scripts because of the webpage was either updated or not loading properly, our assertions would catch those problems.

# How did you test each functionaity with different test data


# Discuss advantages and disadvantages of Selenium vs. Sikulix
### Selenium
Advantages include thorough documentation, easy to use interface and effective playback features.
Disadvantages include resource consumption.

### Sikulix
Advantages are being able to include screenshots of the webpage in the program.
Disadvantages include lack of documentation and having to write the scripts manually.

# How the team work/effort was divided and managed
For the mutation testing, members collaborated to think of how to kill the mutants that survived our original test suite. We used a peer-programming method where one person coded and the rest would provide input.

For the GUI testing, each member developed 2 or more test cases on the same website using the Selenium IDE.

# Difficulties encountered, challenges overcome, and lessons learned
### Difficulties encountered
 - High usage of computer resources (ex. high CPU and GPU usage, high temperatures of internal parts)

### Challenges overcome
 - 
 
### Lessons learned
 - How to use Selenium
 - How to use Pitest
 - How to develop test cases that will kill mutants

# Comments/feedback on the lab itself
Informative lab about how to perform mutation and GUI testing.
