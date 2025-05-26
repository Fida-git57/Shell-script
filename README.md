# Shell-script
What is shell?
	Shell is a program, it will takes the commands whatever the user has typed and it will gives to the OS to execute.
	shell is an interface b/w user and OS
 
--------------------------------------------------------------------------------------------------------------
shells --> commands
to check shell info or how many shells are suppoting by the server --> cat /etc/shells

To display which shell we are using now
	--> echo $SHELL 
		$-->variable 
	without $ symbol we won'ty get any value 
	
What is shell scripting?
	Shell scripting is nothing but a simple file which contains the series of commands.
	
	Shell script extension is ---> .sh 

creat a shell script dir

To run shellscript file no. of ways

. <file_name.sh>
sh file_name.sh

csh file_name.sh
tcsh file_name.sh
ksh file_name.sh

#!/bin/bash   --->shebang line
	it is not mandatory..Ifwe don't specify it by default it will allow only bash .sh..by using this we can run the file by tcsh,csh...
	
Why to run shellscript is debug mode?
	If we are getting some errors in some case then we need to run in debug mode. 
	
How to run in debug mode?
	sh -x <file_name.sh>
	bash -x file_name.sh
sh,bash will support the debug mode 

if specific lines to be run in debug mode
set -x						-->starting debug mode
echo "...."
set +x						-->stopping debug mode
Only these line will run in debug mode.

---------------------------------------------------------------------------------------------------------------------------------
FILE NAME CONVENTIONS:
	A file name can be a maximum of 255 characters
	The name may contain alphabets,digits,dots and underscore
	System commands or linux reserve words can not be used for filename
	It is case sensitive

----------------------------------------------------------------------------------------------------------------------------------
Comments
	Comments gives more understandibility of codes

Types of comments supported by c language
1. Single Line Comments. --> //
       
2. Multi Line Comments. -->/*
	                    ..
   	                    ..
                           */
							
In shell script 
SLC --> #
MLC --><<Fida
	..
	..
	Fida
		
	. Comments are used to escape from the codes
	. This part of the code will be ignored by the program interpreter.
	. Adding comments make things easy for the programmer, while editing code in future.

---------------------------------------------------------------------------------------------------------------------	
VARIABLES
	It is a memory location where we can store the values.

2types of variables
	1. Sytem Defined VARIABLES
	2. User Defined VARIABLES
	
Sytem Defined VARIABLES
	This variables are created and assigned by the system
	There are many sdv are there
TO know how many SDV are there and what are the SDV:
	env
	printenv

 			
variable name			
SHELL=/bin/bash
	   variable value
		
HISTSIZE --> Dfault 1000 (History size)
To change it --> export HISTSIZE=<VAlue e.g 200> for once
to change permanently --> .bash_profile

	export --> default values of system defined var values.
	E.g : export HISTSIZE=200

If we know only the variable name and need to display the corresponding variable value then
		echo ${variable name}

PWD	--> Variable name 
pwd --> Command name

USER DEFINED VARIABLES
	The variables which are created and maintained by the users in script.
	There is no command to see all the UDV
	It should be in lower case
	While executing there should'nt be any gap b/w udv and values.

How we create UDV
E.G:

int a = 10
int b = 20
String Name ="ABC"

shell script--->
a=10
b=20
Name=ABC

echo $a
echo $b
echo $Name

System variables
	Created and maintained by linux bash shell itself.
 
 ----------------------------------------------------------------------------------------------------------------------------
 COMMAND LINE ARGUMENTS
	During shell script execution, values passing  through command prompt is=a called as command line 
arguments.

For eg., while running a shell script, we can specify the command line arguments as 
"sh scriptfile.sh aeg1 arg2 arg3"
 
while using command line args follow imp points
	-we can specify n number of args, there is no limitation.
	-Each arg is separated by space.

Eg., describes the command line arguments.
File name: commandlinearg.sh

#!/bin/sh
#Number of args on the command line.
echo '$#:'$#
#process no. of current process.
echo'$$:'$$
#Display the 3rd arg on the command line, from left to right.
echo'$3:'$3
#Display the name of current shell or program
echo'$0:'$0
#display all the args on the command line using * symbol.
echo'$*:'$*
#Display all args on the command line using @ symbol.
echo'$*:'$@

-------------------------------------------------------------------------------------------------------------------------------------
Diff b/w $* aND $@
	The collection of arguments in $* is treated as one string, whereas the 
collection of arguments in $@ is treated as separeate srtrings.

Escape character
	when using echo -e, we can use special characters:
	\\	backlash
	\a	alert(BEL)
	\b	backspace
	\c	supress trailing newline
	\f	form feed
	\n	new line
	\r	carriage return
	\t	horizontal tab
	\v	vertical tab

Egs.,
	File name: escape_characters.sh
	echo-e"Displaying backlash:\\"
	echo-e"Making sound(alert):\a"
	echo-e"Displaying backspace:\b"
	echo-e"Displaying single quote:\'"
	echo-e"Displaying double quote:\" "
	echo-e"new line:\n"

----------------------------------------------------------------------------------------------------------------------
Strings:
	Strings are scalar and there is no limit to the size of a string.
      Any characters, symbols, or words can be used to make up of string.

Defining a string:
By using single or double quatations 
"Double quotes"-Anything encloses in double quotes removed meaning of that characters (except\ and $)
'single quotes'- enclosed in single quotes remains unchanged.
`back quote`- to execute command
Example:
FileName: quotes.sh 
#!/bin/bash 
single='Single quoted' 
double="Double quoted" 
echo $single
echo $double

Save the above example script as quotes.sh 
chmod 755 quotes.sh
./quotes.sh

--------------------------------------------------------------------------------------------------------------------------
STRING FORMATTING

Character Description
-n Do not output the trailing new line.
-e Enable interpretation of the following backslash escaped characters in the strings:
\a alert (bell)
\b backspace
\c suppress trailing new line
\n new line
\r carriage return
\t horizontal tab
\\ backslash
Example:

#!/bin/bash
echo -e "Hello \t Welcome to Linux Shell Scripting"

-----------------------------------------------------------------------------------------------------------------------------
ARITHEMATIC OPERATIONS
	We use the keyword "expr" to perform arithematic operations.

Syntax:
expr op1 math-operator op2

Example:

FileName: arithmetic_operations.sh
$ expr 3 + 2
$ expr 3 - 2
$ expr 10 / 2
$ expr 20 % 3
$ expr 10 \* 3
$ echo `expr 3 + 2`

In shell scripting we will be using the echo command to print the result of the arithmetic operations.

Note:
If you use echo command, before expr keyword we use ` (back quote) sign. Here both double and single quote will not give you the desired result.
Try the following commands:

$ echo "expr 3 + 2" # Result expr 3 + 2
$ echo 'expr 3 + 2' # Result expr 3 + 2
$ echo `expr 3 + 2` # Result 5

From the above example, we see that if we use double or single quote, the echo command directly prints " expr 3 + 2 ".
To get the result of this expression, we need to use the back quote.

---------------------------------------------------------------------------------------------
User Interaction using read command

In some cases the script needs to interact with the user and accept inputs. 
In shell scripts we use the read statement to take input from the user.

read : read command is used to get the input from the user (Making scripts interactive).

Following shell script demonstrates the take the input from user and display that back to user.
File Name: readName.sh
#!/bin/bash
#Author: Fida Arooj

#Date: 18th May 2025.

echo "Please enter your name:" 
read userName

echo The name you entered is $userName 

Run the above script as follows:
#./readName.sh

Output:
Please enter your name: Fida Arooj
The name you entered is Fida Arooj

File Name: readMultipleValues.sh
#!/bin/bash
#Author: Fida Arooj. 
#Date: 18th May 2025.

echo "Please enter DevOps Tools/Techniques:"
read devOpsTool1 devOpsTool2 devOpsTool3 devOpsTool4 devOpsTool5

echo The DevOps Tools/Techniques you entered are $devOpsTool1 , $devOpsTool2 ,
$devOpsTool3 , $devOpsTool4 ,$devOpsTool5

Output:
Please enter Devops Tools/Techniques:
GitHub Maven Jenkins Chef Tomcat
The Devops Tools/Techniques you entered are GitHub, Mven, Jenkins, Chef, Tomcat

---------------------------------------------------------------------------------------------
Debugging

For debugging the shell we can use –v, -x and –n options. General syntax is as follows. 

#sh << options >> << script name >>
(OR)
#bash << options >> << script name >>

-x : Display commands and their arguments as they are executed.
-v : Display shell input lines as they are read.
-n : Read commands but do not execute them. This may be used to check a shell script for syntax errors

Following shell script will accept the numbers from command prompt and, it will display the sum of those two numbers.

--------------------------------------------------------------------------------------------------
Input - Output redirection in Shell Scripts

Using shell scripts, we can redirect - the output of a command to a file 
or
- redirect an output file as an input to other commands.

In Shell script there are mainly 3 types of redirect symbols as follows.

1. > Redirect standard output 

Example:
ls > ls-file.txt

The above command will redirect the output of the " ls " to the file " ls-file ".
If the file " ls-file " already exist, it will be overwritten. Here you will loose the existing data.

2. >> Append standard output 
Example:
date >> ls-file.txt

The output of the date command will be appended to the file " ls-file ".
In this case you will not loose any data. The new data gets added to the end of the file.

3.< Redirect standard input 
Example:
cat < ls-file.txt

This redirection symbol takes input from a file.
In the above example the cat command takes the input from the file " ls-file " and displays the "ls-file" content.

--------------------------------------------------------------------------------------------------------

if control statement:

Syntax:

if condition
then
	Display commands list if condition is true.
else
	Display commands list if condition is false.
fi

Note: if and then must be separated, either with a << new line >> or a semicolon (;). 
Termination of the if statement is fi.

E.G.,
File Name: FindBiggestNumber.sh

if [ $n1 -gt $n2 ] && [ $n1 -gt $n3 ] 
then
echo "$n1 is the biggest t number" 
elif [ $n2 -gt $n1 ] && [ $n2 -gt $n3 ]
then
echo "$n2 is the biggest t number" 
elif [ $n3 -gt $n1 ] && [ $n3 -gt $n2 ] then
echo "$n3 is the biggest number"
elif [ $1 -eq $2 ] && [ $1 -eq $3 ] && [ $2 -eq $3 ] 
then
echo "All the three numbers are equal"
else
echo "I can not figure out which number is bigger"
fi
Run:

sh findbiggestNumber.sh 1 2 3
Output:
3 is the biggest number

-----------------------------------------------------------------------------------------------------
for loop 
Syntax:
	for (condition ) 
	do
		execute here all command/script until the condition is
		not satisfied.(And repeat all statement between do and done)
	done

Example:
FIleName: for_loop.sh
echo "Can you see the following:"

for (( i=1; i<=5; i++ ))
do
  echo $i
  echo ""
done

Output:

Can you see the following:
1
2
3
4
5

------------------------------------------------------------------------------------
while loop 
Syntax:
while [ condition ]
	do
	  command1 
	  command2 
	  command3
	  ..
	  ....
	done

Example:
i=5
while test $i != 0 
do
  echo "$i" 
  echo " "
  i=`expr $i - 1`

Output:
5
4
3
2
1

------------------------------------------------------------------------------------------
Functions:

When your scripts start to become very large, you may tend to notice that you are repeating code 
more often in your scripts. You have the ability to create functions inside of your script to help 
with code reuse. Writing the same code in multiple sections of your script can lead to severe
maintenance problems

Syntax:

function_name() {

Commands to be execute here...

}

Example:
Write a function to display Welcome to Shell script! message.

FileName: FunctionExample.sh 
#!/bin/bash

greetfn(){

echo "Welcome to Shell script! "

}

echo "Calling greetfn()!" 
greetfn

----------------------------------------------------------------------------------------------
Pipes:

A pipe is nothing but a temporary storage place where the output of one command is stored and
then passed as the input for second command. Pipes are used to run more than two commands 
(Multiple commands) from same command line.

Pipelines connect the standard output of one command directly to the standard input of another. 
The pipe symbol (|) is used between the commands

Filters

A filter is a program that accepts input, transforms it or does something useful with it and outputs 
the transformed data. Some important filter commands are awk, tee, grep, sed, spell, and wc.

Example:
ls -l | grep -a "^d" | tee dir.lst | wc -l 

what the above command does:
The ls command lists all the files and directories. The grep command takes only the directories.
Using tee command, we write the result to the file " dir.list " and the wc -l prints the total number
of lines in that file.

We have used 3 filters in the above example:
The grep, tee and wc.

------------------------------------------------------------------------------------------------
Process

Process is kind of program or task in execution.
Each command, program or a script in linux is a process.

Managing a process
You might have seen some process taking long time to execute. You can run such process in the background.

Example:

ls/-R|wc-l

The above command can be used to find the total count of the files on your system. 
This takes a long a time, so to get the command prompt and to start an other process, 
you can run the above command in background

Running a process in background

ls/-R |wc-l &

The ampersand (&) at the end of command tells the shell to run the command in background. 
You will a number printed on your screen. It is the process Id.
So for each process you will have a process Id.















