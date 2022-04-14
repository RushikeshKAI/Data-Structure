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


**Binary Search Trees, Traversals and Balancing**
QUESTION 3: you are tasked with developing a fast in-memory data structure to manage profile information 
(username, name and email) for 100 million users. It should allow the following operations to be performed efficiently:

    1. Insert the profile information for a new user.
    2. Find the profile information of a user, given their username
    3. Update the profile information of a user, given their username
    4. List all the users of the platform, sorted by username
Assuming that usernames are unique.

The various functions can be implemented as follows:

    1. Insert: Loop through the list and add the new user at a position that keeps the list sorted.
    2. Find: Loop through the list and find the user object with the username matching the query.
    3. Update: Loop through the list, find the user object matching the query and update the details
    4. List: Return the list of user objects.

Analyze the algorithm's complexity and identify inefficiencies:
    
The operations insert, find, update involves iterating over a list of users, in the worst case, they may take up to N iterations to return a result, where N is the total number of users. list_all however, simply returns the existing internal list of users.

Thus, the time complexities of the various operations are:

    1. Insert: O(N)
    2. Find: O(N)
    3. Update: O(N)
    4. List: O(1)

Verify that the space complexity of each operation is O(1).

**Balanced Binary Search Trees**

For use case, require the binary tree to have some additional properties:

Keys and Values: Each node of the tree stores a key (a username) and a value (a User object). Only keys are shown in the picture above for brevity. 
A binary tree where nodes have both a key and a value is often referred to as a map or treemap (because it maps keys to values).
Binary Search Tree: The left subtree of any node only contains nodes with keys that are lexicographically smaller than the node's key, 
and the right subtree of any node only contains nodes with keys that lexicographically larger than the node's key. 
A tree that satisfies this property is called a binary search trees, and it's easy to locate a specific key by traversing a single path down from the root note.
Balanced Tree: The tree is balanced i.e. it does not skew too heavily to one side or the other. 
The left and right subtrees of any node shouldn't differ in height/depth by more than 1 level.

Height of a Binary Tree
The number of levels in a tree is called its height. As you can tell from the picture above, each level of a tree contains twice as many nodes as the previous level.

For a tree of height k, here's a list of the number of nodes at each level:

    Level 0: 1
    
    Level 1: 2
    
    Level 2: 4 i.e. 2^2
    
    Level 3: 8 i.e. 2^3
    
    ...
    
    Level k-1: 2^(k-1)

If the total number of nodes in the tree is N, then it follows that

N = 1 + 2^1 + 2^2 + 2^3 + ... + 2^(k-1)

We can simplify this equation by adding 1 on each side:
    
    N + 1 = 1 + 1 + 2^1 + 2^2 + 2^3 + ... + 2^(k-1) 
    
    N + 1 = 2^1 + 2^1 + 2^2+ 2^3 + ... + 2^(k-1) 
    
    N + 1 = = 2^2 + 2^2 + 2^3 + ... + 2^(k-1)
    
    N + 1 = = 2^3 + 2^3 + ... + 2^(k-1)
    
    ...
    
    N + 1 = 2^(k-1) + 2^(k-1)
    
    N + 1 = 2^k
    
    k = log(N + 1) <= log(N) + 1 

Thus, to store N records we require a balanced binary search tree (BST) of height no larger than log(N) + 1. 
This is a very useful property, in combination with the fact that nodes are arranged in a way that makes 
it easy to find a specific key by following a single path down from the root.


**Binary Tree**

**QUESTION 2**: Implement a binary tree using Python, and show its usage with some examples.


**Traversing a Binary Tree**
QUESTION 3: Write a function to perform the inorder traversal of a binary tree.

QUESTION 4: Write a function to perform the preorder traversal of a binary tree.

QUESTION 5: Write a function to perform the postorder traversal of a binary tree.

A traversal refers to the process of visiting each node of a tree exactly once. 
Visiting a node generally refers to adding the node's key to a list. 
There are three ways to traverse a binary tree and return the list of visited keys:

Inorder traversal

    Traverse the left subtree recursively inorder.
    Traverse the current node.
    Traverse the right subtree recursively inorder.

Preorder traversal

    Traverse the current node.
    Traverse the left subtree recursively preorder.
    Traverse the right subtree recursively preorder.

Postorder traversal
    
    Traverse the right subtree recursively postorder.
    Traverse the current node.
    Traverse the left subtree recursively postorder.

**Height and Size of a Binary Tree**

QUESTION 6: Write a function to calculate the height/depth of a binary tree

QUESTION 7: Write a function to count the number of nodes in a binary tree

The height/depth of a binary tree is defined as the length of the longest path from its root node to a leaf. It can be computed recursively.


**Binary Search Tree (BST)**

A binary search tree or BST is a binary tree that satisfies the following conditions:

    1. The left subtree of any node only contains nodes with keys less than the node's key
    2. The right subtree of any node only contains nodes with keys greater than the node's key

QUESTION 8: Write a function to check if a binary tree is a binary search tree (BST).

QUESTION 9: Write a function to find the maximum key in a binary tree.

QUESTION 10: Write a function to find the minimum key in a binary tree.

**Storing Key-Value Pairs using BSTs**

Recall that we need to store user objects with each key in our BST. Let's define new class BSTNode to represent the nodes of our tree. 
Apart from having properties key, left and right, we'll also store a value and pointer to the parent node (for easier upward traversal).

**Insertion into BST**

QUESTION 11: Write a function to insert a new node into a BST.



