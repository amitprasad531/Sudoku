# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: Constraint propagation is the iterative application of a set of constraints on the values of variables in order to achieve a feasible solution, if possible. Potentially, constraint propagation enables us to iteratively change and simplify the problem to to identify solutions.

The naked twins strategy for generating Sudoku solutions applies two sets of constraints that narrow the possible set of solutions:
(1) We identify two peer squares (or boxes) that are constrained to the same two values. These pairs of peers are called naked twins. This dependency means that each of the naked twin can only assigned one of the two values.
(2) An important implication of the previous conclusion is that none of their (naked twins') peers can be assigned either of the two values. This means that we can eliminate these two values from the possible set of solutions from the remaining peers.

In the programming assignment we first have to identify naked twins. This requires extracting all squares with exactly two possible values in a list. If there is more than one such square we check to see if any of the squares in the list is a potential naked twin, creating a list of lists in the process. Next we iterate through the list of naked twin pairs (if any) and remove their two values from the set of possible values for their common peers. We have to first identify common peers that the naked twins belong to (row, column, diagonal, or 3x3 box). Then loop through the two values to remove them from peers.

# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: The use of constraint propagation to solve a diagonal sudoku is similar to that for solving a regular sudoku. The only difference is that now we define two more units along the main diagonals of the 9x9 grid. One of the key implications for this is that an extra list of peers are created for boxes along these diagonals. This has the effect of adding an extra constraint on the values that the diagonal boxes can contain. For example, the box 'A1' is now constrained by values along its row[A1, A2, ..., A9], column[A1, B1, ..., I1], 3x3 box[A1, A2, A3, ..., C3], as well as values along the diagonal[A1, B2, ..., I9].  

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - You'll fill this in as part of your solution.
* `solution_test.py` - Do not modify this. You can test your solution by running `python solution_test.py`.
* `PySudoku.py` - Do not modify this. This is code for visualizing your solution.
* `visualize.py` - Do not modify this. This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the ```assign_values``` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.  

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.  

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.

