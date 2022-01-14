
# Lab Report 1

## Installing VS Code

I already had VS Code installed on my computer prior to taking this class, but these steps detail how I went about installing it when I did for the first time.

In order to download and install it on my computer, I visited the [VS code website](https://code.visualstudio.com) and downloaded the version for the specific operating system I was using which is macOS. The application was ready for me to use immediately after installing.

![Image](/img/VSCode-Website.png)

---
<br/>

## Remotely Connecting

In order to remotely connect to a server, because I was using macOS, I did not need to install OpenSSH. Instead, I simply found my course-specific account for CSE 15L using the [account lookup tool](https://sdacs.ucsd.edu/~icc/index.php) on the UCSD Educational Technology Services website.

![Image](/img/CSE15L-Account-Lookup.png)

In order to actually remotely connect to a server in the CSE building, I began by opening a terminal in VS Code and typing the following command for my course-specific account:

> `$ ssh cs15lwi22apg@ieng6.ucsd.edu` 

*The three letters following 'wi22' in the command will change depending on the account you are using.*

I was then prompted with a message in my terminal asking if I wanted to continue, and after I confirmed by typing yes, I had successfully connected to the server:

![Image](/img/Remote-Connect.png)

---
<br/>

## Trying Some Commands!

After remotely connecting to the server, I tried some basic commands in the terminal such as `cd`, `ls`, and more. I compared running these commands on my computer (the client) vs the remote server. 

| **Client** |
|--------|
| ![Image](/img/Client-Terminal-Cmds.png)|

| **Server** |
|--------|
| ![Image](/img/Server-Terminal-Cmds.png)|


After attempting both, I observed that the output for these commands varies depending on which computer you are currently logged into, as each contains different files and directories.

---
<br/>

## Moving Files with SCP

The `scp` (secure copy) command allows users to securely copy files between two 

In order to attempt to move files between the client and the server using the `scp` command, I began by creating a new java file called `WhereAmI.java` on my computer (the client). Next, in the terminal from the directory in which I created this file, I ran the following command:

> `scp WhereAmI.java cs15lwi22zz@ieng6.ucsd.edu:~/`

After executing this command and logging back into the CSE server and using `ls`, I was able to see that the file was accessible from the server, meaning the move was successful.

![Image](/img/scp-Command.png)

---
<br/>

## Setting an SSH key

SSH keys allow you to log in and execute commands such as `scp` on a remote server without being prompted to enter a password and log in every time you do so. Creating an SSH key creates two files, a public and private key, which take the place of a password and allow you to log in to a server automatically.

In order set up an SSH key for my account, I used the following command:
> `$ ssh-keygen`

This command created two new files on my computer (the public and private keys) which are stored in the `.ssh` directories of the computer.

Next, I copied the public key over to my user account by using the following command:

`$ scp /Users/anishdevineni/.ssh/id_rsa.pub cs15lwi22apg@ieng6.ucsd.edu:~/.ssh/authorized_keys`

After doing this, when I attempted to log back into my user account on the server, I observed that I was not prompted for a password anymore (as seen below), which cut the login process by more than half.

![Image](/img/SSH-key-Login.png)

---
<br/>

## Optimizing Remote Running

There are several ways to make running commands on a remote server faster and more efficient. I attempted several of these methods, including wrapping commands in quotes to log in, run the command, and log out automatically, and also utilizing semicolons to run multiple commands in one line. Both optimizations are possible in one line, as shown below.

`$ ssh cs15lwi22apg@ieng6.ucsd.edu "javac WhereAmI.java; java WhereAmI"`

*Output:*

![Image](/img/Command-Optimizations.png)
