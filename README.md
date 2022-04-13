# datastructure
Data Structure and Algorithms Problem statement with examples

Problem statement solved with Linear and Binary search and tests its space and time complexity analysis with python
Note: Run each file separately to see output on terminal

Prerequisites:
    IDE(default Pycharm)
    virtualenv
    install required packages from requirement.txt file using below command
    > pip install -r requirement.txt
    Basic programming known with Python (variables, data types, loops, functions)
    Some mathematics part
    Running on your computer locally, execute single file code.
    
**QUESTION 1: Alice has some cards with numbers written on them. She arranges the cards in decreasing order, and lays them out face down in a sequence on a table. She challenges Bob to pick out the card containing a given number by turning over as few cards as possible. Write a function to help Bob locate the card.**

**Problem Solution:** 
    We need to write a program to find the position of a given number in a list of numbers arranged in decreasing order. We also need to minimize the number of times we access elements from the list.

    Input

        cards: A list of numbers sorted in decreasing order. E.g. [13, 11, 10, 7, 4, 3, 1, 0]
        query: A number, whose position in the array is to be determined. E.g. 7

    Output

        position: The position of query in the list cards. E.g. 3 in the above case (counting from 0)

Here's the test case described in the example above.

    cards = [13, 11, 10, 7, 4, 3, 1, 0]
    query = 7
    output = 3

We'll represent our test cases as dictionaries to make it easier to test them once we write implement our function. For example, the above test case can be represented as follows:

    test = {
    'input': { 
        'cards': [13, 11, 10, 7, 4, 3, 1, 0], 
        'query': 7
    },
    'output': 3
    }

The function can now be tested as follows.

    locate_card(**test['input']) == test['output']

You can find number of test cases declared inside tests.py file and also have large test case to test code complexity

Analyze the algorithm's complexity and identify inefficiencies, if any.
    let's try to count the number of iterations in the algorithm. If we start out with an array of N elements, then each time the size of the array reduces to half for the next iteration, until we are left with just 1 element.

    Initial length - N
    
    Iteration 1 - N/2
    
    Iteration 2 - N/4 i.e. N/2^2
    
    Iteration 3 - N/8 i.e. N/2^3
    
    Iteration k - N/2^k
    
    Since the final length of the array is 1, we can find the
    
    N/2^k = 1
    
    Rearranging the terms, we get
    
    N = 2^k
    
    Taking the logarithm

    k = log N 

Where log refers to log to the base 2. Therefore, our algorithm has the time complexity O(log N). This fact is often stated as: binary search runs in logarithmic time. You can verify that the space complexity of binary search is O(1).

Note: We can test the function by passing the input to it directly or by using the evaluate_test_case function from jovian.
Please do uncomment code where Jovian test cases are imported and implemented in file.  


**Problem Statement : Rotated List**
Question 2: You are given list of numbers, obtained by rotating a sorted list an unknown number of times. Write a function to determine the minimum number of times the original sorted list was rotated to obtain the given list. Your function should have the worst-case complexity of O(log N), where N is the length of the list. You can assume that all the numbers in the list are unique.

    Example: The list [5, 6, 9, 0, 2, 3, 4] was obtained by rotating the sorted list [0, 2, 3, 4, 5, 6, 9] 3 times.

    We define "rotating a list" as removing the last element of the list and adding it before the first element. E.g. rotating the list [3, 2, 4, 1] produces [1, 3, 2, 4].
 
    "Sorted list" refers to a list where the elements are arranged in the increasing order e.g. [1, 3, 5, 7].

Here's the systematic strategy we'll apply for solving problems:

   1. State the problem clearly. Identify the input & output formats.
   2. Come up with some example inputs & outputs. Try to cover all edge cases.
   3. Come up with a correct solution for the problem. State it in plain English.
   4. Implement the solution and test it using example inputs. Fix bugs, if any.
   5. Analyze the algorithm's complexity and identify inefficiencies, if any.
   6. Apply the right technique to overcome the inefficiency. Repeat steps 3 to 6.

We'll express our test cases as dictionaries, to test them easily. Each dictionary will contain 2 keys: input (a dictionary itself containing one key for each argument to the function and output (the expected result from the function). 
Here's an example below.

    test = {
        'input': {
            'nums': [19, 25, 29, 3, 5, 6, 7, 9, 11, 14]
        },
        'output': 3
    }

Example: In the list [19, 25, 29, 3, 5, 6, 7, 9, 11, 14], the number 3 is the only number smaller than its predecessor. 
It occurs at the position 4 (counting from 0), hence the array was rotated 4 times.

If the middle element is smaller than its predecessor, then it is the answer. 
However, if it isn't, this check is not sufficient to determine whether the answer lies to the left or the right of it. 
Consider the following examples.

[7, 8, 1, 3, 4, 5, 6] (answer lies to the left of the middle element)

[1, 2, 3, 4, 5, -1, 0] (answer lies to the right of the middle element)


