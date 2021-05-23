# Vulnversity
## Task 1: Deploy the machine
Connect to our network and deploy this machine. If you are unsure on how to get connected, complete the OpenVPN room first.
___
Deploy the machine
> No Answer Needed


## Task 2: Reconnaissance
Gather information about this machine using a network scanning tool called `nmap`. Check out the [Nmap](https://tryhackme.com/room/furthernmap) room for more on this!

Don't have a Linux machine with nmap on? Deploy your own [AttackBox](https://tryhackme.com/my-machine) and control it with your browser.
___
Scan this box: nmap -sV <machines ip>

nmap is an free, open-source and powerful tool used to discover hosts and services on a computer network. In our example, we are using nmap to scan this machine to identify all services that are running on a particular port. nmap has many capabilities, below is a table summarising some of the functionality it provides.
  
| nmap flag	| Description
| :---  | :---
| -sV	| Attempts to determine the version of the services running
| -p \<x\> or -p-	| Port scan for port <x> or scan all ports
| -Pn	| Disable host discovery and just scan for open ports
| -A	| Enables OS and version detection, executes in-build scripts for further enumeration 
| -sC	| Scan with the default nmap scripts
| -v	| Verbose mode
| -sU	| UDP port scan
| -sS	| TCP SYN port scan

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
Using a fast directory discovery tool called `GoBuster` you will locate a directory that you can use to upload a shell to.
___
Lets first start of by scanning the website to find any hidden directories. To do this, we're going to use GoBuster.

GoBuster is a tool used to brute-force URIs (directories and files), DNS subdomains and virtual host names. For this machine, we will focus on using it to brute-force directories.

Download GoBuster [here](https://github.com/OJ/gobuster), or if you're on Kali Linux 2020.1+ run `sudo apt-get install gobuster`

To get started, you will need a wordlist for GoBuster (which will be used to quickly go through the wordlist to identify if there is a public directory available. If you are using [Kali Linux](https://tryhackme.com/room/kali) you can find many wordlists under `/usr/share/wordlists`.

Now lets run GoBuster with a wordlist: gobuster `dir -u http://<ip>:3333 -w <word list location>`

| GoBuster flag	| Description
| :--- | :---
| -e	| Print the full URLs in your console
| -u	| The target URL
| -w	| Path to your wordlist
| -U and -P	| Username and Password for Basic Auth
| -p \<x\>	| Proxy to use for requests
| -c \<http cookies\>	| Specify a cookie for simulating your auth
> No Answer Needed
  
What is the directory that has an upload form page?
> /internal/
  
  
## Task 4: Compromiser the webserver
Now you have found a form to upload files, we can leverage this to upload and execute our payload that will lead to compromising the web server.
___
Try upload a few file types to the server, what common extension seems to be blocked?
> .php
  
To identify which extensions are not blocked, we're going to fuzz the upload form.

To do this, we're going to use ***BurpSuite***. If you are unsure to what BurpSuite is, or how to set it up please complete our [BurpSuite](https://tryhackme.com/room/rpburpsuite) room first.
> No Answer Needed
  
We're going to use Intruder (used for automating customised attacks).

To begin, make a wordlist with the following extensions in:

Now make sure BurpSuite is configured to intercept all your browser traffic. Upload a file, once this request is captured, send it to the Intruder. Click on "Payloads" and select the "Sniper" attack type.

Click the "Positions" tab now, find the filename and "Add §" to the extension. It should look like so:

Run this attack, what extension is allowed?
> .phtml
  
Now we know what extension we can use for our payload we can progress.

We are going to use a PHP reverse shell as our payload. A reverse shell works by being called on the remote host and forcing this host to make a connection to you. So you'll listen for incoming connections, upload and have your shell executed which will beacon out to you to control!

Download the following reverse PHP shell [here](https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php).

To gain remote access to this machine, follow these steps:
1. Edit the php-reverse-shell.php file and edit the ip to be your tun0 ip (you can get this by going to http://10.10.10.10 in the browser of your TryHackMe connected device).
2. Rename this file to php-reverse-shell.phtml
3. We're now going to listen to incoming connections using netcat. Run the following command: `nc -lvnp 1234`
4. Upload your shell and navigate to `http://<ip>:3333/internal/uploads/php-reverse-shell.phtml` - This will execute your payload
5. You should see a connection on your netcat session
> No Answer Needed
  
What is the name of the user who manages the webserver?
> bill
  
What is the user flag?
> 8bd7...cedb
  
  
## Task 5: Privilege Escalation
Now you have compromised this machine, we are going to escalate our privileges and become the superuser (root).
___
In Linux, SUID (set owner userId upon execution) is a special type of file permission given to a file. SUID gives temporary permissions to a user to run the program/file with the permission of the file owner (rather than the user who runs it).

For example, the binary file to change your password has the SUID bit set on it (/usr/bin/passwd). This is because to change your password, it will need to write to the shadowers file that you do not have access to, root does, so it has root privileges to make the right changes.
  
On the system, search for all SUID files. What file stands out?
> /bin/systemctlj

Its challenge time! We have guided you through this far, are you able to exploit this system further to escalate your privileges and get the final answer?

Become root and get the last flag (/root/root.txt)
> a58f...7fd5
