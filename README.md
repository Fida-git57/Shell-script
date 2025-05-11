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
