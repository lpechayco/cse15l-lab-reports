# Welcome CSE15L Students! 
# My name is Lauren!

<br />

## I will be teaching you how to log into a course-specific account on ieng6.

<br />

## Let's get started:

1) Install Visual Studio Code

<br />

Go to the VScode website [VScodeDownload](https://code.visualstudio.com/download) and follow the instructions on how to install VScode.

<br />

Once you've done that, when you open up VScode, it should look something like this:

<br />

![image](VScodeScreenshot.png)

<br />
<br />

2) Remotely Connecting

<br />

**Only if you're on Windows:**
<br />
You need to download a program called [OpenSSH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse), which allows you to connect your computer to other computers with this kind of account.

<br />

Then, go [here](https://sdacs.ucsd.edu/~icc/index.php) to look up your course-specific account for CSE15L.

<br />

Now, open VScode and open a new terminal by either: Ctrl or Command + `, or use the Terminal → New Terminal menu option, or by clicking the symbols in the bottom left corner.
<br />

The terminal should look something like this: 

<br />

![image](VScodeTerminal.png)

<br />

Now, you should enter your course-specific account information in the terminal. Type "ssh" followed by your specific information. It should look something like this:

<br />

![image](courseSpecificAccountInfo.png)

<br />

Press enter and if this is the first time you are connecting to the server, you will likely get a message like this:

<br />

![image](firstTimeMessage.png)

<br />

Simply type "yes" and press enter, then input your password. Once you're logged in, the whole interaction should look something like this:

<br />

![image](loginPage.png)

<br />

Yay! Now your terminal is connected to a computer in the CSE basement, and any commands you run on your local computer will run on that computer. 
<br />
Your computer is the *client* and the computer in the basement is the *server*. 

<br />

Here is another example of what your log-in should look like:

<br />

![image](myLoginPage.png)

<br />

3) Trying Some Commands

Once you are logged in, try some commands!

<br />

Here are some useful commands:

<br />

![image](commands.png)

<br />

Enter any of these into the terminal. Here is an example of using "ls-lat".

<br />

![image](lslatCommand.png)