# Linux Fundamentals 1
## Task 1: Intro
This room is the first part in the Linux Fundamental rooms designed to teach you about various Linux concepts, and in-built tools. This room covers the following topics:

* Introduction To Linux
* Executing Commands and Man Pages
* Basic File Operators

Deploy the machine attached to this task to get started.
___
Read the above. 
> No Answer Needed

Deploy the machine attached to this task!

NOTE: If you have a machine open in the Welcome room (or any other room) please go to that room and terminate it before deploying the machine attached to this task. These machines are not the same, and only the one attached to this room will work.
> No Answer Needed


## Task 2: Methodology
After careful consideration, I've deemed the best way to go about this is to introduce various concepts in sections, with each section being more complex and requiring knowledge from the previous section. To better enable the transition between section, I've split each section into different users in the VM; when you finish a section you'll have to complete a challenge and then you'll be able to move onto the next section.
___
Read the above.
> No Answer Needed


## Task 3: \[Section 2: Running Commands\] - Basic Command Execution
Now that you've logged into the server, you're gonna wanna do things, and everything that can be done over SSH is done by running commands. To start out, we'll take a look at some of the basic commands, and the first command will be `echo`. Type `echo hello`, and press enter and you'll see your input echoed back at you.


Much like the word it's named after, `echo` returns whatever is inputted into it. Congratulations, you've just ran your first Linux command!
___
Read the above
> No Answer Needed


## Task 4: \[Section 2: Running Commands\] - Manual pages and Flags
Most of the commands you'll learn about have a lot of options that are not immediately known at first glance, these options are known as flags, and have the format `<command> <flag> <input>`. These flags can be learned about using the man command. The `man` command has the format `man <command>`. Therefore, to learn about flags for the echo command, we would type `man echo`. Typing that shows us a nicely formatted document:

We get alot of information, but the flags are stored in the description section. For example the flag to remove the newline is -n. So to output "`Shiba`" without the newline you would type `echo -n Shiba`.        

Note: Some commands support the -h flag, meaning you can type `<command> -h` and get a list of flags and other useful information without using `man`.
___
How would you output hello without a newline
> echo -n hello
  

## Task 5: \[Section 3: Basic File Operations\] - ls
ls is a command that lists information about every file/directory in the directory. Just running the ls command outputs the name of every file in the directory.

As with other commands ls has many flags that can manipulate the output.  For example `ls -a` shows all files/directories including ones that start with `.`
___
What flag ouputs all entries
> -a

What flag ouputs things in a "long list" format
> -l


## Task 6: \[Section 3: Basic File Operations\] - cat
cat short for concatenate, does exactly that, it outputs the contents of files to the console. For example, given a file called a.txt which contains the data "hello", `cat a.txt` would output hello.

Note: cat supports the --help flag meaning that you can see useful flags without going to the man page
___
What flag numbers all output lines?
> -n


## Task 7: \[Section 3: Basic File Operations\] - touch
touch is a pretty simple command, it creates files. Given the command `touch b.txt`, b.txt would be created.
___
Read the above!
> No Answer Needed


## Task 8: \[Section 3: Basic File Operations\] - Running a Binary
Occasionally there will be times when you want to run downloaded or user created programs. This is done by providing the full path to the binary, for example say you download a binary that outputs noot, providing the full path to that binary will execute it. 

Note: A binary is just executable code, think a windows exe file

This seems like a good time to mention Relative Paths! Every time you intend on running the binary, you don't need to provide a full path, you can use Relative Paths.

Relative Paths:
The chart below will assume the current path is /tmp/aa 

| Relative Path	| Meaning	| Absolute Path	| Relative Path	| Running a binary with a Relative Path	| Running A Binary with an Absolute Path
| :--- | :--- | :--- | :--- | :--- | :---
| .	| Current Directory	| /tmp/aa 	| .	| ./hello	| /tmp/aa/hello
| ..	| Directory before the current directory	| /tmp	| ..	| ../hello	| /tmp/hello
| ~	| The user's home directory	| /home/<current user>	| ~	| ~/hello	| /home/<user>/hello

These shortcuts are incredibly efficient, and save time. These shortcuts for every command, so if I were to run `ls.` it would be the same as running `ls <current directory>`
___
How would you run a binary called hello using the directory shortcut . ?
> ./hello
  
How would you run a binary called hello in your home directory using the shortcut ~ ?
> ~/hello
  
How would you run a binary called hello in the previous directory using the shortcut .. ?
> ../hello

  
## Task 9: Binary - Shiba1
Now that you've learned basic file operations, you can solve the first challenge! This challenge is pretty simple, create a file called noot.txt.

Once you're done run the binary and you'll be given the password for the user shiba2!
Note: the name of the binary is shiba1, as shown in the title
___
  
<img src="/beginner/images/Linix-fundamentals-1-task_8.png" height="50%" width="50%"/>

What's the password for shiba2
> pinguftw


## Task 10: su
Now that we have our next user password, it seems like a good time to cover su. su is a command that allows you to change the user, without logging out and logging back in again. For example if you wanted to switch to shiba2 while you're the user shiba1, you would type `su shiba2`. You would then be prompted for a password and if you entered shiba2's password you would then become shiba2
  
Note: Typing `su` on its own is equivalent to typing `su root`.
___
Read the Above. 
> No Answer Needed


## Task 11: Linux Fundamentals
Now that you have some beginner knowledge to using Linux, its time you take it a step further and join the [Linux Fundamentals 2](https://tryhackme.com/room/linux2) room.
___
Join the Linux Fundamentals 2 room, and continue your learning journey: [https://tryhackme.com/room/linux2](https://tryhackme.com/room/linux2)
> No Answer Needed

Terminate the machine.
> No Answer Needed
