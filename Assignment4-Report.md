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
10. [How did you test each functionaity with different test data](#How-did-you-test-each-functionaity-with-different-test-data)
11. [Discuss advantages and disadvantages of Selenium vs. Sikulix](#Discuss-advantages-and-disadvantages-of-Selenium-vs.-Sikulix)
12. [How the team work/effort was divided and managed](#How-the-team-work/effort-was-divided-and-managed)
13. [Difficulties encountered, challenges overcome, and lessons learned](#Difficulties-encountered-challenges-overcome-and-lessons-learned)
14. [Comments/feedback on the lab itself](#Comments/feedback-on-the-lab-itself)

# Introduction

This lab was used to teach students about mutation faults in Java and how to remedy these faults using the PiTest Tool in Eclipse. Furthermore, we learned how to implement GUI automation through Selenium and Sikulix, and compared these tools. Before the lab we were aware of the concepts of mutation testing and automated GUI testing from the course lectures. With the lab we put these concepts into practice with the various aformentioned tools.

# Analysis of 10 Mutants of the Range class

### 1. Incremented (a++) double local variable:

This mutation alters the source code by incrementing the specified local variable (of type double in this case) by 1 after it is passed (post-increment).\
For example if a line of code is: `double result = value` it would be mutated to be `double result = value++`.

In our original test suite this mutant was killed in some cases and survived in others. This was due to whether the change had lasting effects throughout the method or it was overwritten by later code before the return statement.

### 2. Decremented (--a) double local variable:

This mutation alters the source code by decrementing the specified local variable (of type double in this case) by 1 before it is passed (pre-decrement).\
For example if a line of code is: `double resule = value` it would be muated to be `double result = --value`.

In our original test suite this mutant was killed in some cases and survived in others. This was due to whether the change had lasting effects throughout the method or it was overwritten by later code before the return statement.

### 3. Replaced double division with multiplication:

This mutation alters the source code by exchanging the division operator with the multiplication operator in a double division.\
For example if a line of code is: `return value / 2.0` it would be muated to be `return value * 2.0`

In our original test suite this mutant was killed. Since it drastically altered the return value for the mutated method, it was killed by most test cases since they didn't solely test with zeros.

### 4. Replaced double division with modulus

This mutation alters the source code by exchanging the division operator with the modulus operator in a double division.\
For example if a line of code is: `return value / 2.0` it would be muated to be `return value % 2.0`

In our original test suite this mutant was killed. Since it drastically altered the return value for the mutated method, it was killed by most test cases since they didn't solely test with zeros and common multiples.

### 5. negated conditional:

This mutant alters the source code by negating a condition.\
For example if a line of code is: `if (lower > upper)` it would be mutated to be `if (!(lower > upper))`

In our original test suite this mutant was always killed for the methods that were covered. Since branch coverage was 100% this meant that we had test cases that ensured the conditions for the method called were all explored.

### 6. Less than to equal:

This mutant exchanges the "less than" operator with the equality operator "==" in conditional statements.\
For example if a line of code is: `return (value < upper)` it would be mutated to be `return (value == upper)`

In our original test suite this mutant was killed. We had enough coverage for the boudaries of the relevant methods, for all instances to be detected and killed.

### 7. greater than to equal:

This mutant exchanges the "greater than" operator with the equality operator "==" in conditional statements.\
For example if a line of code is: `return (value > lower)` it would be mutated to be `return (value == lower)`

In our original test suite this mutant was killed. We had enough coverage for the boudaries of the relevant methods, for all instances to be detected and killed.

### 8. not equal to equal:

This mutant exchanges the inequality operator "!=" with the equality operator "==", or alternatively it removes the "!" operator if present.\
For example if a line of code is: `if (!contains(value))` it would be mutated to be `if (contains(value))`

In our original test suite this mutant was killed. We had enough branch and conditional coverage for the relevant methods, such that all instances were detected and killed.

### 9. removed conditional - replaced comparison check with false:

This mutant alters the source code by removing conditional statements entirely and replacing them with `false`.\
For example if a line of code is: `if (lower > upper)` it would be replaced with `if (false)`

In our original test suite this mutant was killed in some cases and survived in others. This was often due to the types of assertions in our test cases being too uniform and thus not detecting the unchaging operation of the method under test.

### 10. replaced return value with null:

This mutant alters the source code by exchanging the return value with that of `null`.\
For example if a line of code is: `return range` it would be replaced with `return null`

In our original test suite this mutant was killed. Since many assertions made were checking for specific numerical return values, every instance of this mutation was killed.

# Report all the statistics and the mutation score for each test class

The report summary generated by PiTest of our initial and final mutation scores can be found here for [initial](https://github.com/seng438-winter-2022/seng438-a4-Mik-Ese/blob/main/InitialMutationTestResults.zip) and here for [final](https://github.com/seng438-winter-2022/seng438-a4-Mik-Ese/blob/main/FinalMutationTestResults.zip).

To view results, unzip the desired file and open the `index.html` file.

# Analysis drawn on the effectiveness of each of the test classes

Some of the test classes were able to better find mutants than others. Comparing the original and new mutation scores, certain functions which reused local variables were better at killing mutants. However, most of the functions from the Range class and a few from the DataUtilities class were unable to kill the same type of mutants (ex. post-increment/decrement, condition changes). Due to this, our group needed to design extra test cases which were able to kill these mutants.

# A discussion on the effect of equivalent mutants on mutation score accuracy

Equivalent Mutant are when the source code is modified via mutant testing, but they do not change the original functionality of the program. This means that this mutant will produce correct outputs and will survive the mutant testing, but it is not a bug, as it is equivalent to the original code. This mutant is mainly found in loops, when there is a condition to check when to break out of the loop. This was found in line 104 in `DataUtilities.java`, for the method `clone`. What this means to the overall mutation score is that it is realistically unachievable to get a 100% score, as loops are essential in many programs.

# A discussion of what could have been done to improve the mutation score of the test suites

To improve the mutation scores of the test suite, more tests had to be added that would kill the corresponding mutants. For example, most our original test cases did not kill off the post-increment/decrement mutants. To fix this, we had to create new tests that could check if variables were updated after the line had completed. This was able to kill off most of these mutants. Other mutants also required new test cases that catered to specific behavior in order for them to be killed.

# Why do we need mutation testing? Advantages and disadvantages of mutation testing

Mutation testing allows for developers to see if the current program is able to catch more complex or rare errors. It also can help developers see if conditions for loops or if statements can be exploited. In general, mutation testing is another way to see how faults can be introduced by either the software or users.

The advantages of mutation testing include being able to find more faults, having more metrics to improve test suites and providing a more thorough check of the program's functionality.

The disadvantages of mutation testing include the amount of time and resources needed to implement it. Mutation testing takes a lot of time and a decent amount of computation power to automate, which slows down the development process.

# Explain your SELENUIM test case design process

Our group designed the Selenium test cases by first looking through the websites and seeing what functionality was available. Based on that, we would decide which paths to take in the website. Then, we would start Selenium and record our test cases. After this, we would replay them to check if Selenium was able to record all of the keystrokes and mouse clicks correctly.

# Explain the use of assertions and checkpoints

Assertions and Checkpoints are used to verify certain conditions in GUI Testing. Conditions can include checking if a certain element is on the page, or checking if an element contains a text.
Our group used assertions to see if Selenium clicked the right part of the webpage and if the correct GUI element was available. This would help with error checking the scripts because if the webpage was either updated or not loading properly, our assertions would catch those problems.

# How did you test each functionaity with different test data

### BestBuy

Search: Uses different search results, such as headphones, phones and invalid queries

Shop dropdown: Uses different links, such as Appliances and Computers, Tablets and Accessories in a dropdown menu

Store Locations: Checks store locations in Calgary, AB (10 stores)

Add item to cart: Checks successful addition of headphones to cart

Sales filter: Navigates to washing machines section and applies sales filter

### Walmart

Adding items to cart: tried going to different departments and adding various items to the cart

Deals Search: Navigates deals section and selects item

### Sportscheck

Search Store: Search store location in Edmonton

Switch Store: Tested store switch functionality

Mail List Signup: Checks error message for invalid email, and preentive submission with empty fields

# Discuss advantages and disadvantages of Selenium vs. Sikulix

### Selenium

Advantages include thorough documentation, easy to use UI and being able to replay the scripts in real time (via web browser).
Disadvantages include high resource consumption and slow execution speed.

### Sikulix

Advantages include being able to include screenshots of the webpage in the program.
Disadvantages include lack of documentation and having to write the scripts manually.

# How the team work/effort was divided and managed

For the mutation testing, members collaborated to think of how to kill the mutants that survived our original test suite. We used a peer-programming method where one person coded and the rest would provide input.

For the GUI testing, each member developed 2 or more test cases on the same website using the Selenium IDE.

# Difficulties encountered, challenges overcome, and lessons learned

### Difficulties encountered

-   High usage of computer resources (ex. high CPU and GPU usage, high temperatures of internal parts)

### Challenges overcome

-   Installation of Pitest
-   Compatibility issues of Pitest with Java compiler
-   Identifying why mutants survived

### Lessons learned

-   How to use Selenium
-   How to use Pitest
-   How to develop test cases that will kill mutants

# Comments/feedback on the lab itself

Informative lab about how to perform mutation and GUI testing.
