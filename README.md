Download Link: https://assignmentchef.com/product/solved-cmsc-216-project-1-grades-calculator
<br>
<strong>Overview</strong>

For this project you will write a C program that reads assignment scores and computes numeric grades and statistical information. The objective is to practice functions and arrays.

<ul>

 <li><strong>Obtaining project files</strong></li>

</ul>

Copy the folder project1 available in the 216public projects directory to your 216 directory. This folder has the file (.submit) that will allow you to submit your project.

This project description can be found in the 216public project descriptions directory.

<ul>

 <li><strong>Debugging Guidelines</strong></li>

</ul>

Before looking for help during office hours or posting a message in Piazza, make every attempt to debug your program. Make sure you are familiar with the information provided at <a href="http://www.cs.umd.edu/~nelson/classes/resources/cdebugging/">http://www.cs.umd.edu/</a><a href="http://www.cs.umd.edu/~nelson/classes/resources/cdebugging/">~</a><a href="http://www.cs.umd.edu/~nelson/classes/resources/cdebugging/">nelson/classes/resources/cdebugging/</a>

<ul>

 <li><strong>Specifications</strong>

  <ul>

   <li><strong>Input Data</strong></li>

  </ul></li>

</ul>

Your project will read information about class assignments and compute a numeric score. The data provided consists of:

<ul>

 <li>Number of assignments (<em>N </em>for short)</li>

 <li>Points penalty per day late (<em>P </em>for short)</li>

 <li>Number of assignments to drop (<em>X </em>for short)</li>

 <li>Whether statistical information is to be generated (<em>W</em>)</li>

 <li><em>N </em>lines of assignment information, each consisting of assignment number, score, weight, and days late.</li>

</ul>

The data format is:

<em>P X W</em>

<em>N</em>

Assignment Info #1 // line with assignment number, score, weight (percentage), days late Assignment Info #2

<ul>

 <li>··</li>

</ul>

Assignment Info #<em>N</em>

You can assume that input <em>W </em>is a character, and every other input (<em>P</em>, <em>X</em>, <em>N</em>, and each entry in Assignment Info) is an integer.

The following is an example of the data your program will process:

10 2 Y

4

<h1><a name="_Toc5708"></a>2, 82, 40, 1</h1>

1, 91, 40, 0

4, 84, 10, 3

<h1><a name="_Toc5709"></a>3, 73, 10, 3</h1>

The above data says there is a 10 points penalty per day late, 2 assignments are to be dropped, statistical information is to be generated (Y), and there are 4 assignments in total. The first Assignment Info line says that for assignment number 2, the student’s score is 82, the assignment represents 40% of the student’s grade, and it was submitted 1 day late.

<strong>3.2     Processing</strong>

Your program will compute the numeric score by first dropping the <em>X </em>“lowest valued” (defined below) assignments, and then taking into account days late, penalty per day late, and the weight associated with the assignments. If statistical information is requested, the mean and standard deviation will be computed. For example, for the above data, your program should generate the following output:

Numeric Score: 81.5000

Points Penalty Per Day Late: 10 Number of Assignments Dropped: 2 Values Provided:

Assignment, Score, Weight, Days Late

1, 91, 40, 0

<a href="#_Toc5708">2, 82, 40,                                                                        1</a>

<a href="#_Toc5709">3, 73, 10,                                                                        3</a>

<a href="#_Toc5710">4, 84, 10,Mean: 65.0000, Standard Deviation: 18.2346                                                                          3</a>




Regarding the data and processing:

<ol>

 <li>Use double as your floating-type (e.g., double tmp, double numeric score).</li>

 <li>The assignment number is an integer between 1 and <em>N</em>. You can assume <em>N </em>is at least 1.</li>

 <li>Assignment Info lines can be provided in any order of assignment numbers. However they must be printed in increasing order of assignment number. You can assume there are <em>N </em>Assignment Info lines with assignment numbers 1 through <em>N </em>(so no missing or duplicated assignment numbers).</li>

 <li>An assignment score is an integer value between 0 (inclusive) and 100 (inclusive). You can assume we provide valid scores.</li>

 <li>The weight is an integer value between 0 (inclusive) and 100 (inclusive). You need to check the that sum of weights for all assignments add to 100. If after reading the data the total weights do not add to 100, your program will generate the error message <strong>ERROR: Invalid values provided </strong>and the program will terminate. The message should be printed on a line by itself.</li>

 <li>Your program should remove the <em>X </em>lowest-valued assignments before performing any numeric score computation. The <strong>value </strong>of an assignment is defined as the assignment score × the assignment weight. You can assume that <em>X </em>will be in the inclusive range 0..<em>N </em>− Note that the number of days late and the penalty per day IS NOT used in order to decide what assignment to drop. If two assignments have the same value (score × weight), drop the one with the lowest assignment number.</li>

 <li>The numeric score is a value between 0 (inclusive) and a 100 (inclusive). For the numeric grade computation, adjust the score for an assignment based on the number of days late and the points penalty per day late. An assignment score is set to 0 if the assignment’s score becomes less than 0 after the late penalty is applied. This adjusted score along with the assignment’s weight will allow you to compute the numeric score.</li>

 <li>If any assignment is dropped, the sum of assignment weights will, nearly always, not correspond to 100.</li>

 <li>For <em>W </em>equal to either ’Y’ or ’y’, print statistical information. Any other character for <em>W </em>means that no statistical information is to be generated.</li>

 <li>For the computation of the mean and standard deviation, apply the late penalty but do not drop any assignments (even if there was a assignment drop request). In addition, do not use weights for the computation of mean and standard deviation.</li>

 <li>You don’t need to implement a sorting algorithm. The assignment number can be used to generate the index where an assignment should be.</li>

</ol>

<strong>3.3      Functions Requirements</strong>

<ol>

 <li>You must have at least two other functions in addition to main.</li>

 <li>One of your functions must take at least one array as a parameter.</li>

</ol>

<strong>3.4    Other</strong>

<ol>

 <li>Use %5.4f as the format for a float.</li>

 <li>The maximum number of assignments (<em>N</em>) in the input is 50.</li>

 <li>IMPORTANT: You may not use the following C constructs. If you do you will lose significant credit. a. C structures.

  <ol>

   <li>Global variables.</li>

   <li>Two-dimensional (2D) arrays.</li>

   <li>An array of pointers to arrays. We consider them 2D arrays.</li>

   <li>Dynamic memory allocation (e.g., malloc, calloc).</li>

  </ol></li>

 <li>To use the sqrt function or any function from the math library, include the file &lt;math.h&gt; and compile with the -lm option (e.g., gcc grades.c -lm). You can find additional information about the math library by using the linux man pages (“man sqrt” on grace).</li>

 <li>You must name your C file grades.c, otherwise it will not compile on the submit server.</li>

 <li>You may not use the qsort function.</li>

 <li>If you decide to use the indent tool make sure you define the appropriate alias as specified in the indent utility info.txt file that can be found in the grace info folder.</li>

 <li>You need to use #define (e.g., instead of 50 use #define to define a symbolic constant).</li>

 <li>A standard deviation calculator can be found at: <a href="https://www.mathsisfun.com/data/standard-deviation-calculator.html">http://www.mathsisfun.com/data/standard-deviation-calculator.html</a>

  <ul>

   <li><strong>Compilation</strong></li>

  </ul></li>

</ol>

Make sure your gcc alias has been set as defined at <a href="http://www.cs.umd.edu/~nelson/classes/resources/setting_gcc_alias/">http://www.cs.umd.edu/</a><a href="http://www.cs.umd.edu/~nelson/classes/resources/setting_gcc_alias/">~</a><a href="http://www.cs.umd.edu/~nelson/classes/resources/setting_gcc_alias/">nelson/classes/resources/setting_gcc_alias/</a>

<ul>

 <li><strong>Execution</strong></li>

</ul>

We will use input and output redirection in order to execute your program. For example, assuming data is present in the public01.in file, we will run your program as follows: a.out &lt; public01.in. You can compare the results of your program against expected results by using the diff command. Information about the diff command can be found at <a href="http://www.cs.umd.edu/~nelson/classes/resources/cdebugging/diff/">http://www.cs.umd.edu/</a><a href="http://www.cs.umd.edu/~nelson/classes/resources/cdebugging/diff/">~</a><a href="http://www.cs.umd.edu/~nelson/classes/resources/cdebugging/diff/">nelson/classes/resources/cdebugging/diff/</a><a href="http://www.cs.umd.edu/~nelson/classes/resources/cdebugging/diff/">.</a> Make sure you remove output files created while using output redirection. If your code has bugs (e.g., infinite loop) you may create large files that impact grace’s quota.

<ul>

 <li><strong>Style grading</strong></li>

</ul>

For this project, your code is expected to conform to the following style guidelines:

<ul>

 <li>Your code must have a comment at the beginning with your name, university ID number, and UMD Directory ID (i.e., your username on Grace).</li>

 <li>Avoid lines longer than 80 columns. You can check your code’s line lengths using the linecheck program in grace. Just run “linecheck filename.c” and it will report any lines that are too long.</li>

 <li>Do not use global variables.</li>

 <li>Feel free to use helper functions for this project.</li>

 <li>Each function must have, at a minimum, a comment describing its purpose and operation. If you use a complicated algorithm to implement a function, you definitely need an extra comment explaining the complicated steps of your algorithm.</li>

 <li>Follow the C style guidelines available at: <a href="http://www.cs.umd.edu/~nelson/classes/resources/cstyleguide/">http://www.cs.umd.edu/</a><a href="http://www.cs.umd.edu/~nelson/classes/resources/cstyleguide/">~</a><a href="http://www.cs.umd.edu/~nelson/classes/resources/cstyleguide/">nelson/classes/resources/cstyleguide/</a></li>

 <li>TAs will look at each of the following items while grading your style:

  <ol>

   <li>Good names for variables, constants, and functions. The only place where a variable name with a single character is acceptable is the iteration variable of a for loop; otherwise you need to have descriptive variable names. If something represents the mean, called it mean, not m.</li>

   <li>Good indentation (3 or 4 spaces). Use a proper editor (e.g., emacs, vim) that assists with indentation. TAs will check your indentation with the emacs editor.</li>

   <li>If variables have the same type declare them on the same line if possible.</li>

   <li>Leave one blank line between variable declarations and the first line of code in a function.</li>

   <li>Consistent style (e.g., use of curly brackets). Opening brace must be on the same line as conditional or function.</li>

   <li>Do not use CamelCase. Use underscores for multi-word variables. For example, use hot water temperature instead of hotWaterTemperature.</li>

   <li>Define values as constants when needed (do not use variables for constants). Do not use numbers in your expressions if those numbers have a special meaning (e.g., 3.1415); instead define constants (e.g., using #define) for them.</li>

   <li>#defined constants must be in uppercase (e.g., ALL CAPS).</li>

   <li>In your code you should leave one blank space between operators (e.g., x = 5 + 7).</li>

   <li>Leave one space after a comma.</li>

   <li>Use braces; avoid loops and conditionals without them.</li>

  </ol></li>

 <li><strong>Testing</strong></li>

</ul>

Make sure you test your code with different input data sets (sets different from the ones we have provided as public input). You can take one of the provided input files (e.g., public01.in), update it with different values, and use input redirection to generate output. You will need to manually check your results (you may not compare your results with the results of another student’s code). To come up with test cases read the project description carefully. It is best if you think of test cases as you implement your project.

<ul>

 <li><strong>Submission</strong>

  <ul>

   <li><strong>Deliverables</strong></li>

  </ul></li>

</ul>

For this project, the only file that we will grade is grades.c (which <strong>must </strong>be the name of your source file).

<ul>

 <li><strong>Procedure</strong></li>

</ul>

You can submit your project by executing, in your project directory (project1), the <strong>submit </strong>command. This will prompt you for your UMD Directory ID and password, and if all goes well, inform you of a successful submission. You should then log onto the submit server (there is a link on the course website) and check your public test results to be sure that things worked as you expected.

You need to execute submit in the project1 directory, as we gave you a .submit file that allows you to submit. If you did not copy the project1 folder we have provided, you will not be able to submit (you will be missing the necessary .submit file).

Immediately after copying the project1 folder, try to submit your project (even if you have not started). Do not wait until the day the project is due in order to try the submission process.

<ul>

 <li><strong>Possible problem with submit command</strong></li>

</ul>

If you try to submit your project in grace, and you get the error:

”Exception in thread ’main’ java.lang.OutOfMemoryError: unable to create new native thread” then close all terminals windows except one, and try to submit again.