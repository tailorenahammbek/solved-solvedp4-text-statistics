Download Link: https://assignmentchef.com/product/solved-solvedp4-text-statistics
<br>



In this program, you are going to implement a program that analyzes text files to generate some useful statistics. We will provide plain text versions of several books and articles (e.g. Alice in Wonderland, The Gettysburg Address, etc.) for you to analyze using your program.

Text analysis is used in programs all the time. Your program will provide basic statistics like the number of characters, words, and lines, the average word length, and the number of each letter and word length. However, the same technique could be used to collect more statistics and create a program to ascertain characteristics of books and classify them for various purposes.

Booklamp was a recent Boise startup (two of our CS department’s alumni were part of it!) that has created a sophisticated system for analyzing the text in books using techniques similar to what you will be doing in this lab. Booklamp software matches readers to books through an analysis of writing styles. The Booklamp technology allows us to find books that are written with a similar tone, tense, perspective, action level, description level and dialogue level. Booklamp was acquired by Apple on 25th July, 2014.

Objectives

Use arrays.Use command-line arguments.Read from text files using the Scanner class.Parse and analyze text input.Implement an interface.Getting Started

Create a new Eclipse project for this assignment.The easiest way to import all the files into your project is to download and unzip the starter files directly into your project workspace directory (using the command-line or dolphin). The starter files are available here: http://cs.boisestate.edu/~cs121/projects/p4/stubs (You should download p4-stubs.zip).After you unzip the files into your workspace directory outside of Eclipse, go back to Eclipse and refresh your project.Create ProcessText and TextStatistics classes in your project.Start by implementing ProcessText. You can ignore the command-line arguments to start. Just hard-code a file name so you can test your TextStatistics class as you write it. Create a File object and check to see that the file actually exists.If the file does exist, your program will create a TextStatistics object for that file and print out the statistics for the file to the console.If the file does not exist, a meaningful error message needs to be printed to the user.Next you can start implementing TextStatistics according to the specifications.At this point, you should go back and add command-line argument processing to ProcessText as described in the specifications. To make sure it correctly handles command line arguments, run it from the command line with no arguments, files that don’t exist, and files that do exist.Make sure to test your program thoroughly. We are giving you the test program and scripts we will use to grade your program, so take advantage of this and make sure they pass!Specification

Project files

For this assignment you are going to implement two classes. TextStatistics will be the class that reads a text file, parses it, and stores the information about the words and characters in the file. ProcessText is the driver class that gets a list of one or more filenames from the command line and collects statistics on each of the files using an instance of the TextStatistics object.

Classes that you will create: ProcessText.java, TextStatistics.javaExisting interface and class that you will use: TextStatisticsInterface.java, TextStatisticsTest.javaYou should be able to develop this program incrementally in such a way that you can turn in a program that runs even if you don’t succeed in implementing all the specified functionality.

ProcessText.java

The driver class with the main method which processes one or more files to determine some interesting statistics about them.

Command-line validation

The names of the files to process will be given as command line arguments. Make sure to validate the number of command line arguments. There should be at least one file name given.

If no files are given on the command line, your program must print a usage message and exit the program immediately. The message should read as follows.

Usage: java ProcessText file1 [file2 …]This lets the user know how they should run the program without having to go look up the documentation.

Processing command-line arguments

If valid filenames are given on the command line, your program will process each command line argument by creating a File object from it and checking to see that the file actually exists.

If a file does exist, your program will create a TextStatistics object for that file and print out the statistics for the file to the console.If a file does not exist, a meaningful error message needs to be printed to the user. Continue processing the next file. An invalid file in the list should not result in the program crashing or exiting before all files have been processed.The example, CmdLineArgs.java, shows how to use command line arguments in your program. The args parameter of the main method is an array of String objects that contains the command line arguments to the program. For your program, the array should contain the names of the files to be processed.

TextStatistics.java

An instantiable class that reads a given text file, parses it, and stores the generated statistics.

Implement the Interface

Your TextStatistics class must implement the given TextStatisticsInterface (don’t modify the interface, it just provides a list of methods that your class must include).

To implement an interface, you must modify your class header as follows

public class TextStatistics implements TextStatisticsInterface{}Adding “implements TextStatisticsInterface” will cause an error in Eclipse. Select the quick fix option to “Add unimplemented methods” and it will stub out the required methods for you.

Instance variables

Include a reference to the processed File. Include variables for all of the statistics that are computed for the file. Look at the list of accessor methods in the TextStatisticsInterface to determine which statistics will be stored.

Constructor

Takes a File object as a parameter. The constructor should open the file and read the entire file line-by-line, processing each line as it reads it.

You should only have to read through each file once if you are doing this program properly. By the end of the constructor, the TextStatistics object should have collected all of its statistics and calls to its accessor methods will simply return the stored values.Your constructor needs to handle the FileNotFoundException that can occur when the File is opened in a Scanner. Use a try-catch statement to do this. Don’t just throw the exception.As each line is read, collect the following statistics:The number of characters and lines in the file. The number of characters should include all whitespace characters, punctuation, etc. The number of lines should include any blank lines in the file.The number of words in the file.You must use a Scanner on each line to count the number of words in each line of the text file.

To ensure everyone’s results are consistent, you must use the exact delimiter given below rather than making up your own.private static final String DELIMITERS = “[\W\d_]+”;Use useDelimiter(DELIMITERS) on your line Scanner to set the delimiters that the Scanner will use for separating words in the file.

The scanner will not return any of the delimiter characters. For example, using lineScan.next() on the string.

scheme, and the “plan” (for us)will give the following tokens.schemeandtheplanforusA note on words: Using the above delimiters might lead to strange words occasionally. For example, the contraction “we’ve” results in two words “we” and “ve.” This is okay and your program does not have to do anything to fix this.The UseScannerDelimiter.java example shows the different results you get using the default delimiters and user-specified delimiters.

The number of words of each length that appears in the file. Assume that the maximum word length is 23. You do not need to print lengths that have a count of zero.The average word length for the file.The number of each letter that appears in the file – do not separate upper and lower case, just convert all characters to lower case before counting.See LetterCount.java for a similar approach.

Extra credit (+10): Find and report all the line numbers at which the longest word in a file appears. If there are two or more different words of the same longest length, then track the first one only. An ArrayList works well for tracking the line numbers since we don’t know how many occurrences of the longest word will we find ahead of time.Getter (accessor) methods

Implement the accessor methods for the number of characters, number of words, number of lines, average word length and for the arrays that contain the number of words of each length and the number of times each letter occurs in the file.

If you implemented the interface correctly, you should already have methods for these. Just make sure they are returning the correct values. If you are doing your program correctly, most (if not all) of your accessor methods will just contain a single return statement.toString method

Write a toString() method that generates and returns a String that can be printed to summarize the statistics for the file as shown in the sample output.

Testing

You must test your program thoroughly before submitting it. We will be using similar testing strategies when we grade your program, so you should have a good idea whether or not your code will pass our tests before submitting.

TextStatisticsTest.java: Automated testing based on the interface.

We have provided a test program that tests your TextStatistics class using three sample text files. This test program will not compile unless you have properly implemented the required interface. This is available in your starter files.

autograde.sh: Testing based on program output.

autograde.shA shell script (a program made up of shell commands) that you can run to see if your program is going to work with the shell script used for grading the programs.testfile.txt and etextSample text files used by autograde.shtestresultsThe expected output of autograde.sh. Your output should match the contents of this file.To use these files to test your program, copy them into your program directory on onyx and make sure that autograde.sh is executable. (Doing a ls -l on the file should give -rwx——. If the x is missing, type chmod +x autograde.sh).

Now you run the test by typing

./autograde.shIf your program does not compile and run, you need to fix it if you want any points for the program. Make sure all the files have the names specified.

Sample Sessions

Sample output for bad arguments/non-existing files

[<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="bfc6d0caffd0d1c6c7">[email protected]</a> p4]$ java ProcessTextUsage: java ProcessText file1 [file2 …]

[<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="e28f83908b919183a28d8c9b9a">[email protected]</a> p4]$ java ProcessText not-a-file.txtInvalid file path: not-a-file.txt

[<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="fa979b889389899bba95948382">[email protected]</a> p4]$ java ProcessText not-a-file.txt testfile.txtInvalid file path: not-a-file.txtStatistics for testfile.txt==========================================================11 lines79 words465 characters——————————a = 27 n = 25b = 1 o = 26c = 11 p = 5d = 10 q = 0e = 33 r = 21f = 9 s = 30g = 7 t = 35h = 24 u = 7i = 25 v = 1j = 0 w = 10k = 2 x = 1l = 18 y = 2m = 5 z = 0——————————length frequency—— ———1 32 133 244 135 106 27 58 39 110 311 2

Average word length = 4.24==========================================================Sample output for the input file testfile.txt

[<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="661f09132609081f1e">[email protected]</a> p4]$ java ProcessText testfile.txtStatistics for testfile.txt==========================================================11 lines79 words465 characters——————————a = 27 n = 25b = 1 o = 26c = 11 p = 5d = 10 q = 0e = 33 r = 21f = 9 s = 30g = 7 t = 35h = 24 u = 7i = 25 v = 1j = 0 w = 10k = 2 x = 1l = 18 y = 2m = 5 z = 0——————————length frequency—— ———1 32 133 244 135 106 27 58 39 110 311 2

Average word length = 4.24==========================================================Expected output for TextStatisticsTest

[<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="dca5b3a99cb3b2a5a4">[email protected]</a> p4]$ java TextStatisticsTest

Testing on data file:testfile.txt

Passed! getCharCount()Passed! getWordCount()Passed! getLineCount()Passed! getAverageWordLength()Passed! Arrays frequenciesPassed! Letter frequencies

Testing on data file:etext/Gettysburg-Address.txt

Passed! getCharCount()Passed! getWordCount()Passed! getLineCount()Passed! getAverageWordLength()Passed! Arrays frequenciesPassed! Letter frequencies

Testing on data file:etext/Alice-in-Wonderland.txt

Passed! getCharCount()Passed! getWordCount()Passed! getLineCount()Passed! getAverageWordLength()Passed! Arrays frequenciesPassed! Letter frequenciesSubmitting Your Project

Documentation

Javadoc Comments

If you haven’t already, add javadoc comments to your program. They should be located immediately before the class header and before each method. If you forgot how to do this, go look at the Documenting Your Program section from lab.

Have a class javadoc comment before the class.Your class comment must include the @author tag at the end of the comment. This will list you as the author of your software when you create your documentation.Have javadoc comments before every method that you wrote. Comments must include @param and @return tags as appropriate.To build and view your comments, run the following commands.javadoc -author -d doc *.javagoogle-chrome doc/index.htmlREADME

Include a plain-text file called README that describes your program and how to use it. Expected formatting and content are described in README_TEMPLATE. See README_EXAMPLE for an example.

Submission

You will follow the same process for submitting each project.

Open a console and navigate to the project directory containing your source files,Remove all the .class files using the command, rm *.class.In the same directory, execute the submit command for your section as shown in the following table.Look for the success message and timestamp. If you don’t see a success message and timestamp, make sure the submit command you used is EXACTLY as shown.Required Source FilesRequired files (be sure the names match what is here exactly):ProcessText.java (main class)TextStatistics.javaTextStatisticsInterface.java (provided interface)TextStatisticsTest.java (provided test class)autograde.sh (provided test file)READMEDO NOT submit the etext directory. We have our own copies of the test files. The files are large and take up too much space in our submission directories.Section Instructor Submit Command1 Luke Hindman (TuTh 1:30 – 2:45) submit lhindman cs121-1 p42 Greg Andersen (TuTh 9:00 – 10:15) submit gandersen cs121-2 p43 Luke Hindman (TuTh 10:30 – 11:45) submit lhindman cs121-3 p44 Marissa Schmidt (TuTh 4:30 – 5:45) submit marissa cs121-4 p45 Jerry Fails (TuTh 1:30 – 2:45) submit jfails cs121-5 p4After submitting, you may check your submission using the “check” command. In the example below, replace

submit -check