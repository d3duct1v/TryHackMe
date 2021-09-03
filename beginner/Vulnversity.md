# Vulnversity
## Task 1: Deploy the machine

Deploy the machine
> No Answer Needed

## Task 2: Reconnaissance

Scan this box: nmap -sV <machines ip>

There are many nmap "cheatsheets" online that you can use too.
> No Answer Needed

Scan the box, how many ports are open?
> 6

What version of the squid proxy is running on the machine?
> 3.5.12
  
How many ports will nmap scan if the flag -p-400 was used?
> 400
  
Using the nmap flag -n what will it not resolve?
> DNS
  
What is the most likely operating system this machine is running?
> Ubuntu
  
What port is the web server running on?
> 3333

Its important to ensure you are always doing your reconnaissance thoroughly before progressing. Knowing all open services (which can all be points of exploitation) is very important, don't forget that ports on a higher range might be open so always scan ports after 1000 (even if you leave scanning in the background)
> No Answer Needed

## Task 3: Locating directories using GoBuster

What is the directory that has an upload form page?
> /internal/

## Task 4: Compromiser the webserver

Try upload a few file types to the server, what common extension seems to be blocked?
> .php

To do this, we're going to use ***BurpSuite***. If you are unsure to what BurpSuite is, or how to set it up please complete our [BurpSuite](https://tryhackme.com/room/rpburpsuite) room first.
> No Answer Needed

Run this attack, what extension is allowed?
> .phtml
  
What is the name of the user who manages the webserver?
> bill
  
What is the user flag?
> 8bd7...cedb
  
## Task 5: Privilege Escalation
  
On the system, search for all SUID files. What file stands out?
> /bin/systemctlj

Become root and get the last flag (/root/root.txt)
> a58f...7fd5
