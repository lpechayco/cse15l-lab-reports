[back to homepage](index.md)

# Lab Report 1

<br />

## I will be teaching you how to log into a course-specific account on ieng6.

<br />

## Let's get started:

**1) Install Visual Studio Code**

<br />

Go to the VScode website [VScodeDownload](https://code.visualstudio.com/download) and follow the instructions on how to install VScode.

<br />

Once you've done that, when you open up VScode, it should look something like this:

<br />

![image](VScodeScreenshot.png)

<br />
<br />

**2) Remotely Connecting**

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

```
$ ssh cs15lwi22zz@ieng6.ucsd.edu
```

<br />

Press enter and if this is the first time you are connecting to the server, you will likely get a message like this:

<br />

```
⤇ ssh cs15lwi22zz@ieng6.ucsd.edu
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

<br />

Simply type "yes" and press enter, then input your password. Once you're logged in, the whole interaction should look something like this:

<br />

```
⤇ ssh cs15lwi22zz@ieng6.ucsd.edu
The authenticity of host 'ieng6-202.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
Password: 
Last login: Sun Jan  2 14:03:05 2022 from 107-217-10-235.lightspeed.sndgca.sbcglobal.net
quota: No filesystem specified.
Hello cs15lwi22zz, you are currently logged into ieng6-203.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   23:25:01   0  0.08,  0.17,  0.11
ieng6-202   23:25:01   1  0.09,  0.15,  0.11
ieng6-203   23:25:01   1  0.08,  0.15,  0.11

Sun Jan 02, 2022 11:28pm - Prepping cs15lwi22
```

<br />

Yay! Now your terminal is connected to a computer in the CSE basement, and any commands you run on your local computer will run on that computer. 
<br />
Your computer is the *client* and the computer in the basement is the *server*. 

<br />

Here is another example of what your log-in should look like:

<br />

![image](myLoginPage.png)

<br />

**3) Trying Some Commands**

Once you are logged in, try some commands!

<br />

Here are some useful commands:

<br />

```
cd~
cd
ls -lat
ls -a
cp /home/linux/ieng6/cs15lwi22/public/hello.txt ~/
cat /home/linux/ieng6/cs15lwi22/public/hello.txt
```

<br />

Enter any of these into the terminal. Here is an example of using "ls-lat".

<br />

![image](lslatCommand.png)

<br />

**NOTE: To log out of the remote server, either press Ctrl-D or type "exit" into the terminal.**

<br />

**4) Moving Files over SSH with scp**

<br />

It is very useful to be able to copy files from your computer to a remote computer. The command to do this is called "scp", and it is always run from the client (your local computer, not connected to ieng6).

<br />

To test this command, make a sample file to copy. I made a file called "WhereAmI.java" and put the following contents into it:

<br />

```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```

<br />

Then, in the terminal, you should follow this format to run the command:

<br />

```
scp WhereAmI.java cs15lwi22zz@ieng6.ucsd.edu:~/
```

<br />

Here is a screenshot of running the scp command, then logging into the server and running the "ls" command to check that the file was indeed copied over:

<br />

![image](runningSCP.png)

<br />

**5) Setting an SSH key**

Every time we log in, we have to retype or copy-paste our password. This can be time-consuming and inefficient. Thankfully, there's a solution: ssh keys!

The idea behind ssh keys is that a program called ssh-keygen creates a pair of files called the *public key* and the *private key*. Essentially, you make a public key on the server and a private key on the client, and when the ssh command is run, it can use the pair of files in place of your password.

Follow this guide to set up your ssh key:

```
# on client (your computer)
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/joe/.ssh/id_rsa): /Users/joe/.ssh/id_rsa
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/joe/.ssh/id_rsa.
Your public key has been saved in /Users/joe/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:jZaZH6fI8E2I1D35hnvGeBePQ4ELOf2Ge+G0XknoXp0 joe@Joes-Mac-mini.local
The key's randomart image is:
+---[RSA 3072]----+
|                 |
|       . . + .   |
|      . . B o .  |
|     . . B * +.. |
|      o S = *.B. |
|       = = O.*.*+|
|        + * *.BE+|
|           +.+.o |
|             ..  |
+----[SHA256]-----+
```

<br />

**Only if you're on Windows:**

Follow the extra "ssh-add" step [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation).

<br />

Following the set up above created two new files:

the private key: in file "id_rsa"

the public key: in file "id_rsa.pub"

<br />

Now, copy the public key to the .ssh directory of your user account on the server by following these steps:

```
$ ssh cs15lwi22zz@ieng6.ucsd.edu
<Enter Password>
# now on server
$ mkdir .ssh
$ <logout>
# back on client
$ scp /Users/joe/.ssh/id_rsa.pub cs15lwi22@ieng6.ucsd.edu:~/.ssh/authorized_keys
# You use your username and the path you saw in the command above
```

<br />

Once you've completed these steps, just use the "ssh" command like normal and you should be able to log in without having to input your password. It should look something like this:

![image](loginWithoutPass.png)

<br />

6) Optimizing Remote Running

<br />

There are many ways to make running commands in the terminal faster and more efficient. 

For example, you can write a command in quotes after the ssh command to run that command directly and immediately log out of the server afterward.

```
$ ssh cs15lwi22@ieng6.ucsd.edu "ls"
```

<br />

Another example is to use semicolons to run multiple commands on the same line. 

```
$ cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI
```

<br />

Here is an example of the result of running the "ls" command with the ssh command:

![image](fastLogin.png)

<br />

Feel free to try out different combinations and commands to optimize your remote running!

## Hope you enjoyed the tutorial!

[back to homepage](index.md)