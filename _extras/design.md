---
layout: page
title: "Lesson Design"
permalink: /design/
---
## Process Used

This lesson is meant to be used in both [Data Carpentry][dc-website] and 
[Software Carpentry][swc-website] workshops. It's also meant to serve as 
a worked example in [instructor training][instructor-training] of how to 
develop a new lesson. To that end, the outline below was developed using 
a slimmed-down variant of the "Understanding by Design" process. The 
main sections are:

1.  Assumptions about audience, time, etc.
    (The current draft also includes some conclusions and decisions in this 
    section - that should be refactored.)

2.  Desired results:
    overall goals, summative assessments at half-day granularity, what learners 
    will be able to do, what learners will know.

3.  Learning plan:
    each episode has a heading that summarizes what will be covered,
    then estimates time that will be spent on teaching and on exercises,
    while the exercises are given as bullet points.

While it looks like a waterfall process, in practice I did this:

1.  Draft the assumptions.

2.  Do one bullet point for each of several learning milestones.

3.  Draft the desired results.

4.  Update the learning milestones (still as just one bullet point each, 
    no time estimates or exercises).

5.  Get early feedback from four people.

6.  Do a full pass to flesh out the assumptions and add time estimates and exercises.

7.  Ask for feedback and start iterating (mostly to cut things).

At the start of #7 above, the lesson needed 8.5 hours, versus a budget of 6.5.
NumPy went, as did everything to do with running scripts from the command line 
and a bunch of other topics that are useful and important, but not *as* important 
as what's there. This was also the point at which I settled on using the Jupyter 
Notebook (I'd decided on the [Gapminder data][gapminder-data] at the outset to be 
consistent with [Data Carpentry][dc-website]). It took about six hours of work over 
several weeks to get to the point where I felt the lesson was ready for general feedback.

I then solicited feedback from half a dozen experienced instructors. Based on what 
they said, I made further cuts in order to devote more (i.e., more realistic) time 
to basic topics. Defensive programming, debugging, and programming style were merged,
which freed up another half an hour to spend on functions: these are the key to writing 
reusable programs, but defining vs. calling, parameter passing, variable scope, and the 
call stack all need time.

## Stage 1 - Assumptions

*   Audience
    *   Graduate students in numerate disciplines from cosmology to economics
    *   Who understand very basic statistics (mean, standard deviation, correlation coefficient)
    *   And have manipulated data in spreadsheets and with interactive tools like SAS
    *   But have *not* programmed beyond CPD (copy-paste-despair)
*   Constraints
    *   One full day 09:00-17:00
        *   06:30 teaching time
        *   1:00 for lunch
        *   0:30 total for two coffee breaks
    *   Learners use native installs on their own machines
        *   May use VMs or cloud resources at instructor's discretion
        *   But must keep native local install as an option
    *   No dependence on other Carpentry modules
        *   In particular, must not require knowledge of shell or version control
    *   Use the Jupyter Notebook
        *   Authentic tool used by many instructors
        *   There isn't really an alternative
        *   And means that even people who have seen a bit of Python before 
            will probably learn something
*   Data
    *   Use the gapminder data throughout
    *   But break into multiple files by continent
        *   To make display of output from examples tidier (use Australia/New Zealand, 
            which is only two lines)
        *   And allow examples showing use of multiple data sets
*   Focus on Pandas instead of NumPy
    *   Makes lesson usable by both Data Carpentry and Software Carpentry
    *   Genuine novices are likely to want data analysis
    *   And people with some prior experience:
        *   will accept data analysis as an authentic task
        *   And are unlikely to have encountered Pandas,
            so they'll still get something useful out of the lesson
*   Exercises will mostly *not* be "write this code from scratch"
    *   Want lots of short exercises that can reliably be finished in allotted time
    *   So use MCQs, fill-in-the-blanks, Parsons Problems, "tweak this code", etc.
*   Lesson materials
    *   Notes for instructors and self-study will be written in Markdown
        *   We've tried writing/maintaining lessons as Notebooks...
    *   Learners will be provided with one Notebook per episode containing exercises
*   See also:
    *   http://nsoontie.github.io/2015-03-05-ubc/novice/python/Pandas-Lesson.html

## Stage 2 - Desired Results

### Goals

1.  Get learners to the stage decribed in the "Software" section of
    "[Good Enough Practices in Scientific Computing][good-enough]".
    *   Goals
        1.  Make it easy for people (including your future self) to understand and (re)use your code
        2.  Modular, comprehensible, reusable, and testable all come together
    *   Rules
        1.  Every analysis step is represented textually (complete with parameter values)
        2.  Every program or script has a brief explanatory comment at the start
        3.  Programs of all kinds (including "scripts") are broken into functions
        4.  No duplication
        5.  Functions and variables have meaningful names
        6.  Dependencies and requirements are explicit (e.g., a requirements.txt file)
            *   This rule is *not* covered in this lesson
        7.  Commenting/uncommenting are not routinely used to control program behavior
        8.  Use a simple example or test data set to run to tell if it's working at all 
            and whether it gives a known correct output for a simple known input
        9.  Submit code to a reputable DOI-issuing repository upon submission of paper, 
            just like data
            *   This rule is *not* covered in this lesson
2.  Enable them to make sense of other onlines tutorials and resources

### Summative Assessment

*   Midpoint: plot a bar chart showing the average GDP per continent from the data.
*   Final: given a two-page analysis program made up of five functions:
    1.  Modify the input function to read data that is laid out differently (but is still tabular).
    2.  Find and fix a bug in the analysis routine (off-by-one error).
    3.  Add an option to create a plot instead of dumping results as CSV.

### Essential Questions

How do I...

*   ...read, analyze, and visualize a tabular data set?
*   ...process multiple data sets?
*   ...tell if my program is working correctly?
*   ...fix it when it's not?
*   ...find and use software other people have written instead of writing my own?

### Learners Will Be Able To...

*   Run code interactively
*   Run code saved in a file
*   Write single-condition `if` statements
*   Convert between basic data types (integer, float, string)
*   Call built-in functions
*   Use `help` and online documentation
*   Import a library using an alias
*   Call something from an imported library
*   Read tabular data into an array or data frame
*   Do collective operations on arrays and data frames
*   Create simple plots of data in arrays and data frames
*   Interpret common error messages
*   Track down bugs by running small tests of program modules
*   Write non-recursive functions taking a fixed number of named parameters
*   Create literate programs in the Jupyter Notebook

### Learners Will Know...

*   That a program is a piece of lab equipment that implements an analysis
    *   Needs to be validated/calibrated before/during use
    *   Makes analysis reproducible, reviewable, shareable
*   That programs are written for people, not for computers
    *   Meaningful variable names
    *   Modularity for readability as well as re-use
    *   No duplication
    *   Document purpose and use
*   That there is no magic: the programs they use are no different 
    in principle from those they build
*   How to assign values to variables
*   What integers, floats, strings, and data frames are
*   How to trace the execution of a `for` loop
*   How to create and index lists
*   How to trace the execution of `if`/`else` statements
*   The difference between defining and calling a function
*   What a call stack is
*   Where to find documentation on standard libraries
*   How to find out what else scientific Python offers

## Stage 3 - Learning Plan

The original step-by-step learning plan is included below.
It has been superseded by the content of the actual episodes,
but is included for reference.

*   Running and Quitting Interactively (09:00)
    *   Teaching: 15 min (because setup issues)
    *   Exercises: 0 min (accounted for in teaching time - no separate exercise)
        *   Run the Notebook
        *   Create a few Markdown cells
        *   Create and execute a Python cell that prints 1+2
*   Variables and Assignment (09:15)
    *   Teaching: 10 min
    *   Exercises: 10 min
        *   Trace behavior of swapping (`a, b = b, a` the old fashioned way) 
            with an intermediate variable
        *   Calculate elapsed time in seconds using named values for seconds per minute, etc.
*   Data Types and Type Conversion (09:35)
    *   Teaching: 10 min
    *   Exercises: 10 min
        *   Predict result types (or errors) of various operations
        *   Add conversion functions to broken code to make it work
*   Built-in Functions (and Methods) and Help (09:55)
    *   Teaching: 10 min
    *   Exercises: 10 min
        *   Chain calculations with max and min
        *   Find a useful method using help(str)
        *   Parsons Problem to achieve specific results with string methods
*   Error Messages (10:15)
    *   Teaching: 10 min (review of error messages seen to date)
    *   Exercises: 10 min
        *   Diagnose and fix small errors (some syntax, some runtime)
*   Coffee: 15 min (10:35)
*   Libraries (Including Aliases) (10:50)
    *   Teaching: 10 min
    *   Exercises: 10 min
        *   Operations with math library
        *   Look things up in the python.org docs
*   Pandas Data Frames (11:10)
    *   Teaching: 10 min
    *   Exercises: 10 min
        *   Import Pandas
        *   Create and display a data frame
*   Reading Tabular Data (11:30)
    *   Teaching: 5 min
    *   Exercises: 5 min
        *   Read one continent's subset of gapminder CSV data
    *   Callout:
        *   How to read data from Excel spreadsheets via export to CSV
        *   How tor ead data from Excel spreadsheets directly (needs another library)
*   Collective Operations (11:40)
    *   Teaching: 10 min
    *   Exercises: 10 min
        *   Select various subsets of data
        *   Normalize values (scale to 0..1)
*   Lunch: 60 min (12:00)
*   Plotting (13:00)
    *   Teaching: 10 min (to show a variety of plots and debug display problems)
    *   Exercises: 10 min
        *   Plot normalized change in GDP over time (tweaking provided code)
*   For Loops (13:20)
    *   Teaching: 15 min (do *not* introduce lists)
    *   Exercises: 10 min
        *   Reverse a string by repeated append
        *   Trace execution of loop
*   Looping Over Data Sets (13:55)
    *   Teaching: 10 min (use glob to get filenames)
    *   Exercises: 15 min
        *   Count rows of each data set
        *   Check number of columns in each data set is the same
*   Lists (14:20)
    *   Teaching: 10 min
    *   Exercises: 10 min
        *   Indexing exercises
        *   Conversion from list to string and back
        *   Sum values in a list
*   Coffee: 15 min (14:40)
*   Conditionals (15:05)
    *   Teaching: 10 min (inside loop)
    *   Exercises: 15 min
        *   Count vowels
        *   Report badly-sized files inside loop
*   Writing Functions (15:30)
    *   Teaching: 15 min
    *   Exercises: 15 min
        *   Check size of a single data file
        *   Check sizes of all data files in a directory
            *   Write new function using previous function
*   Documentation (16:00)
    *   Teaching: 5 min
    *   Exercises: 10 min
        *   Add docstrings to functions written earlier
*   Programming Style (16:15)
    *   Teaching: 10 min (mostly to introduce checklist)
    *   Exercises: 15 min
        *   Clean up badly-written 20-line program
*   Debugging (16:40)
    *   Teaching: 10 min (divide and conquer)
    *   Exercises: 15 min
        *   Debug three-function program
*   Defensive Programming (17:05)
    *   Teaching: 5 min
    *   Exercises: 10 min
        *   Add assertions to functions based on docstrings
*   Programming with Arrays (17:20)
    *   Teaching: 10 min
    *   Exercises: 10 min
        *   More complicated array indexing
*   Wrap-Up (17:40)
    *   Teaching: 15 min
        *   Overview of key SciPy modules
        *   How to find and install libraries
        *   Running Python from the command line
        *   Other editing tools
    *   Exercises: 0 min
*   Finish (17:55)

[dc-website]: http://datacarpentry.org
[gapminder-data]: http://www.gapminder.org/data/
[good-enough]: https://github.com/swcarpentry/good-enough-practices-in-scientific-computing
[instructor-training]: https://swcarpentry.github.io/instructor-training/
[swc-website]: http://software-carpentry.org
