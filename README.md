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
