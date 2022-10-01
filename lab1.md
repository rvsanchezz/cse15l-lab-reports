# Lab Report 1 - Remote Access and Filesystem

## Finding Your CSE Account
To find your account go [here](https://sdacs.ucsd.edu/~icc/index.php).
Once you find your account you should then reset your password. 

There is an option to keep your TritonLink password the same so be sure to choose that if you wish.
Once it's changed you will get a screen that looks like this:

![changedPassword](<https://user-images.githubusercontent.com/114266346/193379112-73c51c46-f6bc-47d6-8b66-e5eda2df0573.png>)



## Installing Visual Studio Code
Go [here](https://code.visualstudio.com/) to follow instructions on how to download VS Code. There are specfic instructions based on which type of device you own. 
Once downloaded, you can open it and the window should look similar to this.

![newVSWindow](<https://user-images.githubusercontent.com/114266346/193379164-079a4c4e-fdf8-4904-b843-463e606e01c4.png>)



After this you can open a new terminal where you will be running all of your commands.
It should look something like this.


![newTerminal](<https://user-images.githubusercontent.com/114266346/193379189-a77bf221-ce25-4783-ba03-966f48e568ba.png>)



## Connecting Remotely
Since I have a Mac, I followed [these](https://code.visualstudio.com/docs/remote/ssh#_connect-to-a-remote-host) steps to allow access to a remote server on my computer. You will need to do this as well if you haven't already.

The command to access and connect to a remote server will be `ssh` followed by the name of the server. In this case it would be the course specific account name you found earlier followed by "@ieng6.ucsd.edu".

I, unfortunately, was not able to log in using the course specific account so I used my TritonLink login. 
The command you typed into the terminal should look like this:

`ssh cs15lfa22xx@ieng6.ucsd.edu`

*Keep in mind that the xx in the previous command should be different letters corresponding to your personal account.*

This was the first time I've connected to the server so I got a message that looked like this:

```
⤇ ssh cs15lfa22xx@ieng6.ucsd.edu
The authenticity of host 'ieng6-202.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```

I typed in yes and was then prompted to enter my password. This should be the password you just changed. If you are signing in using your TritonLink account it should be your regular password.
The password you type won't appear in the terminal but once you've finished typing, press enter. You should be met with something that looks like this:


![loggedIn](<https://user-images.githubusercontent.com/114266346/193379292-67b5c2e9-975b-4a7c-b6cc-097e2251ad89.png>)

You should now be connected to the remote server!

## Running Commands
You can run some basic commands in the terminal.

-`cd ~` to go back to the previous directory

-`cd` to go to a new directory

-`ls` to list all the folders or files in the current directory

-`cat` to display what is in a file

For example, when I ran the `ls` command I got this:

![lsCommand](<https://user-images.githubusercontent.com/114266346/193379320-be0af2e2-e047-4fb0-a552-b9de0c30b744.png>)


You can see two files appeared.

In order to log out of the remote server and go back to your personal computer you can use either:

-`exit` or

-Ctrl + D

## Moving Files with scp

Now I will teach you how to copy files between the computers using the `scp` command.
This command will be used to copy a file from *your* computer to the *remote* computer.

The first step is to make sure you are logged out of the remote server.

Then you will create a new file called "WhereAmI.java".

You can copy and paste this code into the file

```
class WhereAmI {
  public static void main(String[]args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir")):
  }
}
```


In order to compile and run it, type in the following commands

```
javac WhereAmI.java
java WhereAmI
```

This is what my output was after running it.
![whereAmI](<https://user-images.githubusercontent.com/114266346/193376624-72b0efb1-bf8c-48c6-a733-61525be04143.png>)


Once we know the file was compiled and works, we will copy it to the remote server.

To do this, run this command in your terminal:

`scp WhereAmI.java cs15lfa22xx@ieng6.ucsd.edu:~/`

You will be asked to enter your password for the server. Then you should log in using `ssh` again.
Type `ls` into the terminal after logging in and you should see the WhereAmI.java file listed in the directory.

![newFiles](<https://user-images.githubusercontent.com/114266346/193379675-987a845f-048c-45a2-a0ff-8986530c6342.png>)


You can now compile and run the file on the remote server. In order to do that type the previous commands into the terminal:

```
javac WhereAmI.java
java WhereAmI
```

It should run and give an output that looks like this!
![remote output](<https://user-images.githubusercontent.com/114266346/193377093-9f096026-e2fd-4ebb-8d48-dd3607c6f2de.png>)


## SSH Keys
In order to make login a littler easier we can use ssh keys to create public and private keys that allow you to login to the remote server with these files in lieu of a password.

Type the command `ssh-keygen` into your terminal. (Be sure to be on your computer's server).
This is what the entire process looked like on my end:

![keygen](<https://user-images.githubusercontent.com/114266346/193377272-beef7348-f0e9-416b-bd7d-5b7b902fef22.png>)

To choose the default path when asked which file you want to save the key in, you can just press Enter.

Once that is done you will copy the public key to the `ssh` directory.

To do this follow these steps:
1. Log into the remote server

```
ssh c15lfa22xx@ieng6.ucsd.edu
<Enter your password>
```

2. Then type in the following

```
mkdir .ssh
exit
```

3. Once you're logged out you can copy the public key to the remote server.

```
scp /Users/raquelsanchez/.ssh/id_rsa.pub r6sanche@ieng6.ucsd.edu:~/.ssh/authorized_keys
```

You should be able to log in to the remote server without a password after this.

Unfortunately it did not work with me and I was met with this:
![failedLogin](<https://user-images.githubusercontent.com/114266346/193377476-eb1a9436-2a7b-401e-a6a1-3e1622901008.png>)

I'm not sure what exactly went wrong. I think it may have not copied correctly or I was typing in the wrong commands. 
It just said the public key file wasn't found in the remote server.

## Optimizing Remote Running


It should now be much easier to login to the remote server after not having to enter a password every time.
To make running commands even easier, you can enter multiple commands in the same line.

An example line could be:

`ssh cs15lfa22xx@ieng6.ucsd.edu "javac WhereAmI.java; java WhereAmI"`

This line would log you into the remote server, compile the WhereAmI file, and then run it.

Since I wasn't able to get the keygen to work I still had to enter my password, but other than that I was able to compile and run it in the same line.

![optimize](<https://user-images.githubusercontent.com/114266346/193379840-6130fb7e-fe2b-4341-9a11-92b1c02a79c2.png>)

This is just one example of optimizing the remote server.





