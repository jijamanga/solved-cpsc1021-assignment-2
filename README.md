Download Link: https://assignmentchef.com/product/solved-cpsc1021-assignment-2
<br>
This assignment is designed to provide practice with the following:

<ul>

 <li>Working with Classes</li>

 <li>Working with Composition “has-a” relationship between classes</li>

 <li>Working with vectors</li>

 <li>Formatting output</li>

 <li>Working with multiple files</li>

 <li>Command-line arguments</li>

 <li>Reading data from files</li>

 <li>Sorting data</li>

</ul>

<strong>Overview:</strong>

You are going to read in various appointments from an input file.  You will store the appointment information in a vector.  You will sort and print out the appointment information. You will write three classes for this assignment as well as several helper functions that work with the three classes.

<strong>Classes:</strong>

You will have a CalendarEvent, Date, and Time class. In this document, I will give you the class declaration for each of the three classes. You will need to provide both .cpp and .hpp files for each class. You will also provide a functions.cpp and functions.hpp.

This assignment will give you practice using composition.  Composition is realized when one class “hasan” instance of another class as one of the data members.  The CalendarEvent class will have an instance of Date and an instance of Time as one of the data members. This document will provide the .hpp files. (CalendarEven.hpp, Date.hpp, Time.hpp, and functions.hpp).  You are required to implement the class functions as well as the helper functions in the .cpp files. (CalendarEvent.cpp, Data.cpp, Time.cpp, and functions.cpp). You will also provide a driver.cpp. The driver.cpp file should have minimal amount of code in it.

<strong>CalendarEvent:</strong>

<strong> </strong>

The CalendarEvent class has three private data members: a string for the name of the calendar event, an instance of Date for the date of the event, and an instance for the time of the event.

<table width="672">

 <tbody>

  <tr>

   <td width="672">class CalendarEvent{private:string eventName;Time calTime;         Date calDate;public: CalendarEvent(int month, int day, int year, int hour, int minute,                       string eventName);                    void printCalendar(fstream&amp; out);         bool isEventDateValid();         bool isEventTimeValid();         string getEvent()const; };</td>

  </tr>

 </tbody>

</table>

Notice there is no default constructor for the CalendarEvent class.  You will need to change the provided CalendarEvent constructor so that it will provide the default values in the event an instance of CalendarEvent is created using a default constructor.

<strong>void printCalendar(fstream&amp; out)</strong> –  This function will be used to print the calendar event.  It will need to print the string description of the event (eventName), it will then call the Date’s print function using the instance of the Date class (calDate), it will also use the instance the Time class (calTime) to call the Time’s print function.  Notice the parameter for this function is “fstream rather than ifstream or ofstream”. Fstream allows you to specify if the file pointer being passed to a function is for input or output.  This will become clearer when we go over the functions in the function.hpp file.

<strong>bool isEventDateValid()</strong> – This function is going to use the instance Date to call the isDateValid function.  IsDateValid() will return true or false which will then be returned by isEvenDateValid().

<strong>bool isEventTimeValid() </strong> – This function is going to use the instance of Time to call the isTimeValid function.  IsTimeValid() will return true or false which will then be returned by isEventTimeValid(). <strong>string getEvent() </strong>– This needs no explanation.

<strong>Date:</strong>

The date class has three private data members: int month, int day, and int year, each of which are selfexplanatory.  It also has a public static data member that is an array of strings that represent the string value of each month.

<table width="672">

 <tbody>

  <tr>

   <td width="672">class Date{private:         int month;         int day;int year;  public:Date(int month, int day, int year);         void setMonth(int);         void setDay(int);         void setYear(int);         void setDate(int, int, int);         string getStrMonth();         int getMonth()const;         int getDay()const;         int getYear()const;         void printDate(fstream&amp;);bool isDateValid();         bool isLeapYear();static const string ARRAY[13]; };</td>

  </tr>

 </tbody>

</table>

Again, the Date class only has one constructor. You will need to change the provided Date constructor such that it will provide the default values in the event an instance of Date is created using a default constructor.

The regular setters and getters need no explanation, so I will not spend time on them. Other than to say you may not need this in this project but for practice <strong>I AM REQUIRING YOU TO WRITE THEM</strong>. The function getStrMonth will be used to return the string version of the month.  The input document will provide the string in integer form.  When printing the variable, you are required to print it in the string form.

<strong>void printDate(fstream&amp; out)</strong> – This function is used to print the date portion of the calendar event.

The format of the date should be in the form of:  January 1, 2019

<h1>DUE: November 20, 2019 midnight</h1>

<strong>bool isDateValid() –</strong> This function will be used to ensure the date is a valid date. Such as, making sure the months are with in 1 – 12, the years are between 1900 – 2020 and the day is between 1 and 31. If the month is February the day can only be 29 if it is leap year.  Therefore, you will need to check this. You should also make sure the day given did not exceed the number of days for that month.  If the function fells any of the validity checks you are to return false.

<strong>bool isLeapYear()</strong> – This function will determine if the year read in is a leap year. Look up the rules for determining leap year.

<strong>Time:</strong>

The time class has two data members, each of which are integers.  They represent the hours and minutes of time.

<table width="672">

 <tbody>

  <tr>

   <td width="672">class Time{private:int hour;         int minute;     public:Time(int hours,int mins);         void setHour(int);         void setMinute(int);         void setTime(int, int);         int getHour()const;         int getMinute()const;void printTime(fstream&amp;)const;         bool isTimeValid();};</td>

  </tr>

 </tbody>

</table>

<strong> </strong>Just as with the previous classes discussed, you must modify the Time constructor so that default values are provided through this constructor as well as the regular constructor. The setters and getters are normal, again, you may not use them however, you are required to implement them for practice.

<strong>void printTime(fstream&amp; out) </strong>prints the information pertaining to time.  When printing the time you must convert hours from military time to regular time.  The format of the printing hours:minutes 10:00 pm or am.  If it is noon you are to print 12:00 noon.




<strong>bool isTimeValid() </strong>checks that the hours and minutes are between 0 and 24 and minutes are between 0 and 59. <strong>functions:</strong>

This file provides three functions, readData, checkArguments, and isOpen.

void readData(fstream&amp;, vector&lt;CalendarEvent&gt;&amp;, vector&lt;CalendarEvent&gt;&amp;); void checkArguments(int argc); void isOpen(fstream&amp;, char*);

<strong>void readData(fstream&amp; f, vector&lt;CalendarEvent&gt;&amp; good, vector&lt;CalendarEvent&gt;&amp; bad) </strong>reads the information from the data file. You should read the information one set of data at a time. Once you have read a complete set of data (eventName, date, and time) you should create a temporary instance of CalendarEvent. You should then test the data by calling isEventDateValid() and isEventTimeValid() to check the validity of the date and time information. If both of these functions return true then store the calendarEvent on to the good vector otherwise store the calendarEvent on the bad vector. Depending on how you write your readData you may want to do a little research on the various ways to call ignore. We discussed this function earlier in the semester and I mentioned they there are various ways to call the ignore function. Knowing these different ways may be helpful to you.

<strong>void checkArguments(int argc)</strong> – this function is used to check the number of arguments passed on the command line. You will have 4 arugments: ./executable inputFile goodOutputFile badOutputFile As stated above if the data is not valid you are to store that calendar event on the bad vector otherwise store the data on the good vector.  When printing the information, you will print the good vector to the goodOutputFile.  If the information to be printed is in the bad vector that information will be printed to the badOutputFile. If the correct number of files were not passed to the command line argument you should print a message that says “Not enough command line arguments” and exit the program.

<strong>void isOpen(fstream&amp;, char*)</strong> – this function is used to check if the file opened successfully. This function has two arguments the first is fstream. We learned that input files are usually ifstream, hence “i” for input and ofstream “o” for output.  Fstream can be used for either, however when opening the file you must specify if the file is being opened for input or output. The following are links to help you with this.

<a href="http://www.cplusplus.com/doc/tutorial/files/">http://www.cplusplus.com/doc/tutorial/files/ </a><a href="https://www.tutorialspoint.com/cplusplus/cpp_files_streams.htm">https://www.tutorialspoint.com/cplusplus/cpp_files_streams.htm</a>

If the file did not open correctly you should print a message that tells the user which file did not open, then exit the program. Ex. goodOutput.txt did not open!

<strong>Requirements: </strong>

<ol>

 <li>Implement the classes listed above. (CalendarEvent.hpp, Date.hpp, Time.hpp) You are also to implement the functions in the functions.hpp.</li>

 <li>Sort the good vector and bad vectors by date.</li>

 <li>Print the calendar information for the good vector. The format for the output at a minimal should be as follows:</li>

</ol>

********************************

Pre-registration

January 4, 2019  2:09 pm

********************************

********************************

Faculty Meeting

January 4, 2019  12:00 noon

********************************

********************************

Doctor Appointment Foot

January 8, 2019  3:45 pm

********************************

********************************

Haircut

January 9, 2019  9:02 am

********************************

********************************

TA Meeting

February 4, 2019  11:30 am

********************************

Feel free to be creative with the final output.  I enjoy seeing how creative some students can be with their output.  I may even give a few EC points if you are creative with your output.

Here is an example of the input file:

<strong>Doctor Appointment Foot 11/8/2019 15:45</strong>

<strong>Pre-registration 11/4/2019 14:09</strong>

<strong>Faculty Meeting 11/4/2019 12:00</strong>

<strong>TA Meeting 12/4/2019 11:30 Haircut 11/9/2019 9:02</strong>

<ol start="4">

 <li>Print the calendar information for the bad vector in the same format as above.</li>

 <li>You must use an <strong>iterator</strong> when printing the events in the calendar for the good and bad vectors.</li>

 <li>Create a makefile that has a working make and make run. When I type make run your make file should first compile your files then run the program.</li>

 <li>All of the above are the minimal you are required to do. Feel free to make minimal changes to the functions.  However, I will deduct points if you make do not fulfill the minimal requirements for this assignment.  As an example, if you need to change the prototype of a function feel free to. But don’t do something just do shorten or make the assignment easier, by forgoing some of the listed requirements. An example would be putting all data in public space, etc.</li>

</ol>

<strong>Extra Credit: 5 points</strong>

After sorting the calendar events by date, sort the events by time, such that your calendar entries are sorted by both time and date.

<strong>Formatting, Compiling, and Hand-in Requirements:</strong>

Tar your file <strong>PA2.tar.gz</strong> and submit the file through <strong>hand-in to the folder PA2.  When tarring your file do not tar a PA2 folder.  Please CD into the folder and tar the files in the folder.  I will deduct points if you tar a folder. </strong>If you are doing the EC you must submit a tarred file called <strong>PA2EC.tar.gz</strong> through<strong> hand-in to the folder PA2EC. <u>PLEASE SUBMIT TO ONLY ONE HAND-IN FOLDER.</u></strong>

You should submit the following files.

<ul>

 <li>cpp</li>

 <li>cpp</li>

 <li>hpp</li>

 <li>hpp</li>

 <li>cpp</li>

 <li>hpp</li>

 <li>cpp</li>

 <li>hpp</li>

 <li>cpp  makefile</li>

 <li>Readme that has the following information:</li>

</ul>

o problems you encountered with this assignment o how you solved the problems o your thoughts about the assignment.

<ul>

 <li>With the exception of the makefile, you should have a header in each of your files that contains the following information. If you neglect to place a header in a file, you will receive a 5-point deduction.</li>

</ul>

/**************************/

*Your name                              *

*CPSC1020 Fall19                      *

*Section: &lt;Your section&gt;.        *

*UserName:                              *

*Instructor:  Dr. Yvon Feaster  *

/*************************/

<ul>

 <li>Your program should compile with no warnings and no errors on the School of Computing servers. There will be a substantial point deduction if your program has compile errors. If you made a substantial effort to complete the program, but you have compile errors, you will receive no more than 30 on the assignment. If the program compiles but has warnings, there will be a minimal of 10-point reduction. (The more warnings you have the higher the deductions.)</li>

 <li>You should use meaningful variable names throughout the program.  Your code should be well documented. (comments – see example below)  There should be no line of code longer than 80 characters.</li>

 <li>You should use proper and consistent indention.</li>

</ul>

Failure to do any of the above items will result in a deduction of points for each offense.

Here are some guide lines for documenting the code in this assignment.

Before each function<strong>, in the .hpp files</strong>, you should have a detailed description of what the overall function does. To borrow from another student’s code, here is an example of overall function description.

/* Parameters: img – image_t pointer array holding the image data for

<ul>

 <li>each of the input files</li>

 <li>Return: output – image_t struct containing output image data</li>

 <li>This function averages every pixels rbg values from each of the</li>

 <li>input images and puts those averages into a single output image */</li>

</ul>

You are required to have this type of comment block before each function.

Also, if you include comments in the body of the function (and you should) they should be placed above the line of code not beside the code.

Example:

<table width="516">

 <tbody>

  <tr>

   <td width="206">


    <table width="149">

     <tbody>

      <tr>

       <td width="149">Good//This is a comment if(something){do something;}</td>

      </tr>

     </tbody>

    </table></td>

   <td width="310">


    <table width="252">

     <tbody>

      <tr>

       <td width="252">Badif(something) //This is a comment{do something;}</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>