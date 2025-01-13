EXPERIMENT NO: 01					
AIM: To install python and to run a ‘Hello World’ script.
LO:
Install and configure Python on Windows based machine
Write and execute “Hello World” program using python shell, text editor and IDE.

THEORY: 
	Python is an interpreted, object-oriented, high-level programming language with dynamic semantics. Its high-level built-in data structures, combined with dynamic typing and dynamic binding makes it very attractive for rapid application development, as well as for use as a scripting or glue language to connect existing components together. Python is simple, easy to learn, its syntax emphasizes readability and therefore reduces the cost of programming maintenance. Python supports modules and packages, which encourages program modularity and code reuse. The python interpreter and extensive standard library are available in source or binary form without charge for all major platforms, and can be freely distributed.
PROCEDURE:
Steps to install python on Windows:
 Select version of python to install- The installation procedure involves downloading the official python .exe installer and running it on your system. The version we need depends on what we want to do in python.
 Download python executable installer-
Open your web browser and navigate to the Downloads for Windows section of the official python website. Search the desired version of python. Select windows x86 executable installer and download it.

 Run executable installer-
Run the python installer, once downloaded make sure we select the install launcher for all user and Add Python 3.10 to PATH checkboxes and then select Install Now.
After installation of python the next dialog will prompt you to select whether to disable path length limit. Choosing this option will allow python to bypass the 260-character MAX_PATH limit. Effectively, it will enable python to use long path names.


Verify python was installed on Windows-
Navigate to the directory in which python was installed on the system. Double click on python .exe. It will open a Command Prompt and shows the python version which you have installed. 

Q1) Write a program to print ‘Hello World’ in python.
Source code:
		print(“Hello World”)
OUTPUT:

Running a ‘Hello World’ in cmd line:


Different modes for executing Python program.
 Interactive Mode Programming
 Invoking the interpreter without passing a script file as a parameter brings up the following prompt − $ Python Python 2.4.3 (#1, Nov 11 2010, 13:34:43) [GCC 4.1.2 20080704 (Red Hat 4.1.2-48)] on linux2 Type "help", "copyright", "credits" or "license" for more information. >>> 
Programming with Python (22616) Maharashtra State Board of Technical Education 11 Type the following text at the Python prompt and press the Enter – 
>>> print "Hello, Python!" 
If you are running new version of Python, then you would need to use print statement with parenthesis as in print ("Hello, Python!"); 
However, in Python version 2.4.3, this produces the following result: Hello, Python! 

Script Mode Programming 
Invoking the interpreter with a script parameter begins execution of the script and continues until the script is finished. When the script is finished, the interpreter is no longer active. Let us write a simple Python program in a script. Python files have extension .py.
 Type the following source code in a test.py file: print "Hello, Python!" 
We assume that you have Python interpreter set in PATH variable. 
Now, try to run this program as follows: $ Python test.py
 This produces the following result:
 Hello, Python! 
Let us try another way to execute a Python script. 
Here is the modified test.py file: #!/usr/bin/Python print "Hello, Python!" 
We assume that you have Python interpreter available in /usr/bin directory.
 Now, try to run this program as follows: $ chmod +x test.py # 
This is to make file executable $./test.py This produces the following result – Hello, Python!

CONCLUSION: Hence, we have successfully installed python and successfully executed a simple ‘Hello World’ program.
