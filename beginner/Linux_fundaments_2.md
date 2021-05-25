# Linux Fundamentals 2
## Task 1: Intro
This room is the second part in the Linux Fundamental rooms designed to teach you about various Linux concepts, and in-built tools. This room covers the following topics:

* Linux Operators
* Advanced File Operators

Deploy the machine and SSH into the room as explained in the tasks below using the following credentials (these credentials will be available from the last task of the [Linux Fundamentals Part 1](https://tryhackme.com/room/linux1) room):

* username: shiba2
* password: pinguftw

Please note, unlike the first Linux room you will need to SSH into the machine (there isn't a browser-based machine). Learn how to do this with task 2 and 3.
___
Read the above.
> No Answer Needed

Deploy the machine attached to this task!

NOTE: If you have a machine open in the Welcome room (or any other room) please go to that room and terminate it before deploying the machine attached to this task. These machines are not the same, and only the one attached to this room will work.
> No Answer Needed


## Task 2: SSH - Intro
SSH is the act of remotely accessing a machine. SSH allows you to run commands interactively on the remote machine. This is done through the use of a program on the target machine, which allows the ssh client to interface with the target host.

While the most common usage of a regular operating system is graphical(allowing you to see pictures, web browsers, file managers etc.) SSH works through a command line, meaning anything done on the target machine will be done through a command prompt similar to this.

It may look intimidating at first, but you'll soon find out you can do much of the same functionality that you're able to do using graphical user interfaces!

 It is an invaluable tool, and how you will be accessing this machine to learn and to do the challenges. Depending on the operating system there are different ways of SSHing into a machine. This section will purely focus on the windows way(PuTTY), and after we learn more about linux commands, and how they work, we'll return back to this section and learn about the linux method.

NOTE: Please do not try to SSH into the VM from the Welcome room. You can only access the content in this room from the VM provided in Task One. If you forgot to terminate any other machines, please do so, then press the green button to deploy the Learn Linux VM provided in Task One.
___
Read the above
> No Answer Needed


## Task 3: Putty and SSH
Disclaimer: please do not use putty if you are already on Linux. Use the instructions for the ssh binary down below.

The download for putty can be found [here](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html), once you download it go through the install process. Once you've installed it, open it and you should see this screen

The field that we are most interested in is "Host Name (or IP Address)". This is where the `10.10.20.47` that you got when you deployed the machine comes into play. That's because the format of SSH connections is \<user\>@\<host\>, and in this case host is equal to `10.10.20.47`. The user for this trial will be shiba2, so the completed "Host Name" field should like this (please note that the image uses shiba1 however shiba2 is the correct username).

(Note: the 10.10.10.10 is just an example, and you should replace that with `10.10.20.47`)

From there click open, and you'll be greeted with

Click yes(this prompt is purely for verification purposes) and you'll be prompted for a password (please note that the image uses shiba1 however shiba2 is the correct username):

Enter "pinguftw" and click enter, and you'll have logged in! (please note that the image uses shiba1 however shiba2 is the correct username)

Note: sometimes putty just may not work, in that case follow the ssh binary guide listed below!

As an alternative to putty, you may have an ssh binary on your computer. That binary is accessed by going to your terminal(cmd/MacOS Terminal), and typing ssh.

The syntax on how to use this command is `ssh <user>@<host>`. So to ssh into the machine you'll need to type in `ssh shiba2@10.10.20.47`. It will prompt you for the user password, which in this case is also pinguftw

That's it, you can now run commands interactively!!! :))
___
SSH into the server
> No Answer Needed


## Task 4: \[Section 4: Linux Operators\]: "&&"
&& means as you might expect "and". Meaning && allows you to execute a second command after the first one has executed successfully. Meaning `ls && echo hello` will work fine, but `dljahfrsdkjlhfsdhjklfsdhkljfh && echo hello` will fail.

Note: Since the second command happens after the first command, you can use something created in the first command in the second command.
___
Read the above
> No Answer Needed


## Task 5: \[Section 4: Linux Operstors\]: "&"
Much unlike &&, & has nothing to do with and at all(try saying that 10 times fast). & is a background operator, meaning say you run a command that takes 10 seconds to run, normally you wouldn't be able to run commands during that period; however, with & that command will still execute and you'll be able to run other commands.

Note: I can't exactly show time in an image, but trust me I really did wait the 5 seconds :)
___
Read the above
> No Answer Needed


## Task 6: \[Section 4: Linux Operators\]: "$"
The $ is an unusually special operator, as it is used to denote environment variables. These are variables set by the computer(you can set them yourself but we'll get into that) that are used to affect different processes and how they work. Meaning that if you edit these variables you can change how certain processes work on your computer. For example your current user is always stored in an environment variable called $USER. You can view these variables with the echo command.

Naturally this means environment variables can be used as input for other commands as well, for example say I wanted to create a file which is the name of our current user, I could do `touch $USER`.

Recall that the >> operator appends output to a file.

Environment variables can also be set pretty easily, just running `export <varname>=<value>` will set that as an environment variable
___
How would you set nootnoot equal to 1111
> export nootnoot=1111

What is the value of the home enviornment variable
> /home/shiba2

<img src="/beginner/images/Linux-fundamental-2-task_6.png" height="50%" width="50%"/>

## Task 7: \[Section 4: Linux Operators\]: "|"
Continuing with the trend of very special operators, we have the pipe. The pipe is unique because while operators like >> allow you to store the output of a command, the | operator allows you to take the output of a command and use it as input for a second command.

For example, I can use `cat` to get the output of a file, and pipe that into `grep` to search for a specific string(Note: We will learn more about grep later, but for now just know that it's a command used to find specific strings in an input).

It is worth noting that not all commands support the pipe, and some that do support it require you to use - instead of input, for example `cat -`. So always check to see if the command does support it
___
Read the above!
> No Answer Needed


## Task 8: \[Section 4: Linux Operators\]: ";"
The ; operator works a lot like &&, however it does not require the first command to execute successfully. This means that you can do `dkhsgffgsafgfasdgfasfghkgdsgfs; ls` and you would still see the output of ls.
___
Read the above.
> No Answer Needed


## Task 9: \[Section 4: Linux Operators\]: "\>"
\> is the operator for output redirection. Meaning that you can redirect the output of any command to a file. For example if I were to run echo hello \> file, then instead of outputting hello to the console, it would save that output to a file called file.

It is worth noting that if you were to use this operator on a file that already exists, it would completely erase the contents of that file and replace it with the output from your command
___
How would you output twenty to a file called test
> echo twenty > test


## Task 10: \[Section 4: Linux Operators\]: "\>\>"
\>> does mainly the same thing as >, with one key difference. >> appends the output of a command to a file, instead of erasing it.
___
Read the above
> No Answer Needed


## Task 11: Binary - shiba2
This challenge is pretty simple. The binary is checking to see if the environment variable "test1234" exists, and if it's set equal to the current $USER environment variable.
___
What is shiba3's password?
> happynootnoises

<img src="/beginner/images/Linux-fundamental-2-task_11.png" height="50%" width="50%"/>

## Task 12: \[Section 5 - Advanced File Operations\]: Intro
Much like windows, files have a lot of complexity to them. Multiple different parameters have to be modified to allow certain users to read to files, write to files, and execute certain files. This section will cover modifying these parameters.
___
Read the above.
> No Answer Needed

## Task 13: \[Section 5 - Advanced File Operators\]: A bit of background.
Recall that ls has different flags that allow you to view information about different types of files.

These attributes are(in order) the file permissions, owner of the file, and group that the file is in.

The next few tasks will go over the command to modify these attributes.
___
Read the above!
> No Answer Needed

## Task 14: \[Section 5: Advanced File Operations\]: chown
Recall that ls shows us our username twice.

These attributes are the user, and group attributes resepectively. Recall that we can edit the permissions for these attributes, so it stands to reason that we can also change these attributes. That is done using the chown command, which allows us to change the user and group for any file. The syntax for this command is chown user:group file. For example if we wanted to change the owner of file to shiba2 as well as the group to shiba2, we could use `chown shiba2:shiba2 file`.

Note: You can only use chown if you are "above" that other user, meaning that chown is best done with the root(administrator) user.

You can also use chown without specifying a group. So you can just use chown user file if you only wanted to change the user but keep the group.
___
How would you change the owner of file to paradox
> chown paradox file

What about the owner and the group of file to paradox
> chown paradox:paradox file

What flag allows you to operate on every file in the directory at once?
> -R

## Task 15: \[Section 5: Advanced File Operations\]: chmod
chmod allows you to set the different permissions for a file, and control who can read it. The syntax of this command is typically `chmod <permissions> <file>` . 

The interesting part is how the permissions are set. They're set using a three digit number, where each digit controls a specific permission, meaning the first digit controls the permissions for a user, the second digit controls the permission for a group, the third digit controls permissions for everyone that's not a part of the user or group.

Now the value of the digits control whether they can read, write or execute it or do all three, and to properly calculate it some math needs to be done.

| Digit	| Meaning
| :--- | :---
| 1	| That file can be executed
| 2	| That file can be written to
| 3	| That file can be executed and written to
| 4	| That file can be read
| 5	| That file can be read and executed
| 6	| That file can be written to and read
| 7	| That file can be read, written to, and executed

The way these values are calculated is this. The digit 1 means the file can be executed, the digit 2 means it can be written to, and the digit 4 means it can be read. You get the different permissions by adding these digits together. For example 1+2 is 3 meaning that file can be executed and written to. Now let's see how it all works in perspective.
| Command:	| Meaning
| :--- | :---
| chmod 341 file	| The file can be executed and written to by the user that owns the file. The file can be read by the group that owns the file. The file can be executed by everyone else.
| chmod 777 file	| The file can be read, written to, and executed by the user that owns the file. The file can be read, written to, and executed by the group that owns the file. The file can be read, written to, and executed by everyone else
| chmod 455	| The file can be read by the user that owns the file. The file can be read and executed by the group that owns the file. The file can be read to and executed by everyone else.

ls provides a helpful way of viewing the permissions of files in the current directory.

Recall that file permissions are divided into three sections, user and group and everyone else. The same is true here; however, everything starts from the second hyphen not the first, so we can just forget the first hyphen for now. Note that everything is in sequential order, so the first three characters control permissions for the user, the second three characters control permissions for the group, and the final three characters control permissions for everyone else

rw means as you might expect "read and write", meaning the user has read write perms to the file. Following that logic, that means members of the group and everyone else have only read perms. To convert that to numbers the permissions for that file in number form are 644. We can test this by trying to change the permissions

hen we try to change the perms to 644 nothing happens because the perms are already 644. The interesting part is while we can write data to .profile with echo while the perms are 644, we can't when we change the perms to 544, because we took away our own write perms. Following that logic, that means we can completely lock ourselves out of writing to a file we already own!

Note: It is possible to give someone no perms to a file, You can just put 0 as the digit. 770 Means that everyone that isnt a part of the user or group cant do anything to the file.
___
What permissions mean the user can read the file, the group can read and write to the file, and no one else can read, write or execute the file?
> 460

What permissions mean the user can read, write, and execute the file, the group can read, write, and execute the file, and everyone else can read, write, and execute the file.
> 777

## Task 16: \[Section 5: Advanced File Operations\]: rm
Let's take a break from all the permissions and math, and look at something that can completely destroy your whole Linux system if used carelessly! rm as you might have guessed means remove, and that's exactly what it does.

As you can imagine this is incredibly dangerous, as you can remove some very important files, and render your system completely unusable. It is not worth noting that you need write permissions to the file to deleted so you cant just delete any file if you're a regular user.
___
What flag deletes every file in a directory
> -r

How do you suppress all warning prompts
> -f

## Task 17: \[Section 5: Advanced File Operations\]: mv
mv allows you to move files from one place to another. The syntax for the command is `mv <file> <destination>`. so if I wanted to move a file to my home directory I could type `mv file ~`.

Note: You can also use mv to change the name of file, `mv file ~/ghfds` will rename file to ghfds.
___
How would you move file to /tmp
> mv file /tmp

## Task 18: Linux Fundamentals 3
Now that you have some intermediate knowledge to using Linux, finish the Linux series and join the [Linux Fundamentals 3](https://tryhackme.com/room/linux3) room.
___
Join the Linux Fundamentals 3 room, and finish learning Linux: https://tryhackme.com/room/linux3
> No Answer Needed
