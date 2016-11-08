# 06_Lab
Main Lab #6 - Plinko With Functions
Remember that the style guide has been updated (particularly for "constants and magic numbers" and for "test cases". In addition this is the first time that the function section of the style guide comes into play. Please read those three sections over carefully before beginning this lab.
Background

You may have felt some frustration in writing your solution for the plinko lab because there were parts of your code that you had to duplicate in two or three places. Functions allow us to remove this duplication. More importantly, functions allow us to actually give our program a manageable structure; breaking up a large problems into several smaller problems.

For this lab we will re-write the plinko lab using functions and add a few new features. Note also that most programming in the real world is the modification of existing programs rather than writing entirely new programs. In this lab you will also have opportunity to get experience with that.

Functions are also useful for dealing with errors, such as user input errors. As explained in the style guidelines, in general it is best to deal with errors as soon as possible. In this lab you will make functions for user input which check for user input errors and re-prompt as needed.
Requirements
Part 1 - Refactoring (27 points)

    "Refactor" your Lab 4 code (i.e. preferably do not rewrite Lab 4 from scratch) using functions. Wikipedia explains that "Code refactoring is the process of restructuring existing computer code... Advantages include improved code readability and reduced complexity... Typically, refactoring applies a series of standardised basic micro-refactorings, each of which is (usually) a tiny change in a computer program's source code that ... preserves the behaviour of the software". In the end we really cannot tell if you refactored your lab 4 code or just re-wrote it from scratch, but we encourage you to start with your code for lab 4 and move the code around to achieve a simpler, better program. Before refactoring, you are strongly encouraged to COPY your Lab 4 code into a new solution for Lab 6 (rather than to edit your Lab 4 code directly). This way, if your Lab 6 code gets too scrambled, you still have your Lab 4 code from which to start over. In particular we are expecting to see functions for:
        Computing the amount of prize money won for a single chip given the slot the chip ended up in-- this function must be defined as "double ComputeWinnings(int slot) {... your code here ...}. This just needs to implement the fact that if the chip ends up in slot 0 you get $100.00, if it ends up in slot 1 your get $500.00, etc. (See the original plinko lab for the complete list of these values).
        Simulating one chip falling-- you will have to use your discretion on how you set this up, but it should make both the "Drop a single chip into one slot" option and the next function (Simulating multiple chips falling) easier to write. This function must make use of the "ComputeWinnings" function described above.
        Simulating multiple chips falling-- similarly this function should make both the "Drop multiple chips into one slot" option and a new "Drop multiple chips into each slot" option (described below) easier to write. This function must make use of the "Simulating one chip falling" function described above.

    Your Lab 6 solution must include the major features of Lab 4, however do not print the path for the single drop case.
    Add a new menu item for "Drop multiple chips into each slot", but you do not have to implement it yet. You will implement it in Part 3.
    We will also change the error handling, so do not worry about that for Part 1.

Part 2 - Better Error Handling (27 points)

Add a function for getting the number of chips and a function for getting the slot number. Within these functions check for user input error and reprompt until the user provides valid input. You must be able to recognize erroneous input like "-1", "Not even a number", and in the case of a slot number, invalid input like "9". You may assume that there will be no real-valued inputs like "2.3" Note that due to the improved error handling approach, some of the error messages have been modified.

Add a similar function for the menu too, reprompting if bad input is given.
Part 3 - Functions and the Power of Code Reuse (21 points)

In this part of the lab, you will take advantage of functions to add an additional menu option to your Plinko program, without having to duplicate code from the other menu options.

    Add a new menu option 3 that allows the user to drop the same number of chips into each of the 9 slots. For example, if the user enters 5, you simulate dropping 5 chips into each of the 9 slots.
    Prompt the user to enter one number, which is the number of chips to drop into every slot. If the number of chips is non-positive, reprompt until you get valid input (hint: use the function you wrote in Part 2)
    For each slot, report the total and average amount of money won for all chips dropped into that slot.

Implementation

You must include the random seed in the main function. Normally we would use "srand(time(0))" to get (more nearly) random behavior. but so that our output will match yours, you must use srand(42) in the code you submit.

If you think about it for a minute you might realize that you could use a single function for the error testing in Part 2. Obviously it would need additional parameters to work as required in each case, but it is an interesting possibility. You may do so if you wish.
Items Graded by the TA's Inspection (25 points)

    Adherence to style guidelines. Note this is the first time that the function section of the style guide comes into play, so read that section over carefully before beginning the lab.

    New functions for
        Computing the amount of prize money won for one chip given the slot it ended up in (called "ComputeWinnings") (5 point deduction if missing)
        Simulating one chip falling (must use "ComputeWinnings") (5 point deduction if missing)
        Simulating multiple chips falling (must use "Simulate one chip falling") (5 point deduction if missing)
        New functions for menu, slot and chip input, with error handling. It could be a single function with additional parameters as noted in the implementation section (5 point deduction if missing)

Notes

The test cases start with just the input part, so you can start there and then build your solution step by part. Also, you can test your code as many times as you like.

Remember to review the functions section in the style guide. Note that one of the function style expectations is "Make sure that your naming of functions and parameters are sufficiently clear that you rarely need a comment header to describe the function and parameters."
Sample Output

Welcome to the plinko simulator!

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot
3 - Drop multiple chips into each slot

Enter your selection now: 56

INVALID SELECTION.  Please enter 0, 1, 2 or 3
Enter your selection now: 1

*** DROP SINGLE CHIP ***

Which slot do you want to drop the chip(s) in (0-8)? 10

INVALID SLOT, please try again.
Which slot do you want to drop the chip(s) in (0-8)? 5

WINNINGS: $1000.00

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot
3 - Drop multiple chips into each slot

Enter your selection now: 2

*** DROP MULTIPLE CHIPS ***

How many chips do you want to drop (>0)? -3

INVALID NUMBER OF CHIPS, please try again.
How many chips do you want to drop (>0)? 345

Which slot do you want to drop the chip(s) in (0-8)? 0

Total Winnings on 345 chips: 272100.00
Average winnings per chip: 788.70

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot
3 - Drop multiple chips into each slot

Enter your selection now: 3

How many chips do you want to drop (>0)? 500

*** SEQUENTIALLY DROP MULTIPLE CHIPS ***

Total Winnings on slot 0 chips: 421200.00
Average winnings per chip: 842.40

Total Winnings on slot 1 chips: 602200.00
Average winnings per chip: 1204.40

Total Winnings on slot 2 chips: 775000.00
Average winnings per chip: 1550.00

Total Winnings on slot 3 chips: 1211300.00
Average winnings per chip: 2422.60

Total Winnings on slot 4 chips: 1188500.00
Average winnings per chip: 2377.00

Total Winnings on slot 5 chips: 1029500.00
Average winnings per chip: 2059.00

Total Winnings on slot 6 chips: 891900.00
Average winnings per chip: 1783.80

Total Winnings on slot 7 chips: 521200.00
Average winnings per chip: 1042.40

Total Winnings on slot 8 chips: 344800.00
Average winnings per chip: 689.60


MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot
3 - Drop multiple chips into each slot

Enter your selection now: 0

GOODBYE!
