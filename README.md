# { Terminal Basics Exercises. }

Write the following terminal commands to perform the following tasks:

### Part I

1. make a directory called first

* mkdir first

3. change directory to the first folder

* cd first

5. create a file called person.txt

* touch person.txt

7. change the name of person.txt to another.txt

* mv person.txt another.txt

9. make a copy of the another.txt file and call it copy.txt

* copy another.txt copy.txt

11. remove the copy.txt file

* rm copy.txt

13. make a copy of the first folder and call it second

* cp -r first second

15. delete the second folder

* rm -rf second

### Part II

1. What does the man command do? Type in man rm. How do you scroll and get out?

* The man command brings up the manual page for the command in question.  Down or up arrows to scroll, q to quit out of the man page. 

3. Look at the man page for ls. What does the -l flag do? What does the -a flag do?

* -a lists all files and folders including hidden ones, and -l provides a detailed list

5. Type the following command to download and save the contents of google.com: curl https://www.google.com > google.html

* curl https://www.google.com > google.html

7. Use less to look at the contents of google.html.

* less google.html

9. Look at the man page for less. Read the section on /pattern. Search for the text hplogo in the google.html file.

* less -p hplogo google.html

11. How do you jump between words in the terminal?

* opt left/right

13. How do you get to the end of a line in terminal?

* ctrl + e

15. How do you move your cursor to the beginning in terminal

* ctrl + a

17. How do you delete a word (without pressing backspace multiple times) in terminal?

* opt + del

19. What is the difference between a terminal and shell?

* A terminal is a program and more specifically it’s an emulation of a terminal to access a shell environment.  The shell is a language, essentially, whether that be bash, zsh, tcsh etc. which allows you to issue commands, run scripts, and interact with files on your computer

21. What is an absolute path?

* It’s the full path to a location starting from the root (/) directory

23. What is an relative path?

* It’s a path that is relative to your current location in the directory tree.

25. What is a flag? Give three examples of flags you have used.

* A flag is an option that you pass to a command to specify what kind of output you are looking for.  -a and -l for ls are quite common. -r is very common for recursively copying or deleting everything inside a folder and it’s subfolders.  

27. What do the r and f flags do with the rm command?

* -r is recursive removal and -f will force removal

 

 

# { Permissions, Redirection, and Piping Exercise. }

### Part I (Permissions and links)

Write terminal commands to do the following:

1. Create a file called restricted.txt.

* touch restricted.txt

3. Change the permissions on the restricted.txt file to allow the owner to read and write to the restricted.txt file. Do this using the Octal Notation

* chmod 600 restricted.txt

5. Change the permissions on the restricted.txt file to only allow the owner, group and everyone to read and write and execute the restricted.txt file. Do this using the Symbolic notation.

* chmod a+rwx restricted.txt

7. Create a folder called secret_files. Inside the secret_files folder create a file called first_secret.txt and another folder called classified. Inside of the classified folder create a file called super_secret.txt.

* mkdir secret_files
* touch secret_files/first_secret.txt
* mkdir secret_files/classified
* touch secret_files/classified/super_secret.txt

9. Change the permissions on the secret_files to only allow the owner and group to read, write and execute in all the files and folders inside of secret_files. Do this using the Octal Notation.

* chmod -R 770 secret_files

11. Create a hard link for the restricted.txt called hard_link.

* ln restricted.txt hard_link

13. Create a symbolic link for the classified folder called classified_link.

* ln -s secret_files/classified classified_link

### Part II (Piping and Redirection)  

Write the following terminal commands to do the following

1. Sort vegetables.txt.

* sort vegetables.txt

3. Count the number of lines in vegetables.txt.

* wc -l vegetables.txt

5. Create a file called vegetables_sorted.txt which contains all the unique vegetables sorted in ascending order in vegetables.txt (do this without the touch command).

* cat vegetables.txt | sort | uniq > vegetables_sorted

7. Create a file called last_three.txt which contains the last three vegetables in the vegetables.txt file (do this without the touch command).

* cat vegetables.txt | tail -n 3 > last_three.txt

9. Count the number of lines the word "Broccoli" appears on (using wc and grep).

* cat vegetables.txt | grep "Broccoli" | wc -l



# { Intermediate Terminal Exercises. }

### Part I

Answer the following questions:

1. Create an environment variable called FIRST_NAME and set it equal to your first name (this does not need to be permanent)

* export FIRST_NAME=Peter

3. Print the FIRST_NAME variable

* print $FIRST_NAME or echo $FIRST_NAME

5. Print out the $PATH variable

   * echo $PATH

6. What is the $PATH variable?

* The $PATH variable stores program files for easy reference in the terminal

8. Why would you want to create an environment variable?

* It makes our lives easier so we can reference file or folder locations (folders actually are files too) without having to type them out everytime

10. How do you permanently save environment variables?

* By modifying your shell config file (.zshrc or .bashrc).  These files are essentially shell scripts that run as soon as the shell is started.  The list of commands inside the script run and establishes our shell environment for that session.  

12. What is a process?

* A computer program currently being executed

14. How do you list all processes running on your machine?

* ps -ax

16. What is a PID?

* Process ID

18. How do you terminate a process?

* Use kill, or kill -9

20. What is the difference between kill and kill -9?

* kill will send a termination signal to a running process.  If that process is unresponsive, it’s very likely this won’t work, and kill -9 is absolute

22. What grep flag allows for case insensitive search?

* -i

24. What grep flag allows for a certain number of lines before the match?

* -B

26. What grep flag allows for a certain number of lines around the match?

* -C

28. What grep flag allows for a certain number of lines after the match?

* -A

30. What grep flag allows for full word search?

* -w

32. What grep flag shows you the line number of a match?

* -n

### Part II

Write the following terminal commands to do the following (assume that instructors.txt is an imaginary file):

1. Find all files inside the Desktop folder that have a name of "learn."

* find ~/Desktop -name “learn”

3. Find all files inside the Desktop folder that start with a "P."

* find ~/Desktop -name “P.*”

5. Find all files inside the Desktop folder that end with .txt.

* find ~/Desktop -name “*.txt”

7. Find all files inside the Desktop/views folder that have the name data somewhere in their filename.

* find ~/Desktop/views -name “*data*”

9. Inside of the instructors.txt file, output the number of times the word "Elie" appears.

* grep -c “Elie” instructors.txt

11. Inside of the instructors.txt file, list all matches for any full word that starts with a capital "P."

* grep -w “P.*” instructors.txt

13. Inside of the instructors.txt file, list all the line numbers for any full word that starts with a "z" (it should match regardless of upper or lower case).

* grep -ni “z.*” instructors.txt