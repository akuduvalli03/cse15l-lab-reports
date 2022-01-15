# Lab Report Week 2: Loggings into an account on `ieng6`

## Installing VSCode 

![Image](images/vscode_open.png)
* VSCode is a code editor that will make your life easier. Install VScode [here](https://code.visualstudio.com/). 
* Once you download VSCode, open VSCode. The open page should look something like the image above. 

---

## Remotely connecting to the server
* Open a new terminal window in VSCode. Since I am on a mac, I dont have to download ssh, but windows users can over [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse).
* To find your account for whichever course, search your username [here](https://sdacs.ucsd.edu/~icc/index.php). You may have to change your password to activate the account; I know I did. It might take a while to get activated. 
* After activating your account for a given course, enter **ssh [your account]** to connect to the ieng6 server remotely. 
```
$ ssh cse15lwi22aaw@ieng6.ucsd.edu
```
* follow the prompts (answer yes) and then you will be promted to enter in you password. It is your ucsd login password. 
* You output should be similar to this image--if so, you have connected to the server!


![Image](images/sshworking.png)

---

## Trying a few commands 
* Here are a few commands that I tried once I logged into the server. 
```
cd ~
cd 
ls -a
ls -lat
```

![Image](images/try_out_linux_commands.png)

* based on the output, I've concluded that `cd ~` and `cd ` will return to the root directory (which I was already in in the following screenshot), `ls -lat` will display all the folders abd files with timestamps and extra information of the current directory, and `ls -a` displays all directories that begin with a **.** or a **..**. 

---

## Moving Files With `scp`
* you can work on files remotely from the client side then copy them onto a server. Once way to do this is through the `scp` command. The way that you write the command is `scp [filename] [username]:~/` 
* For example, when I save the file *whereami.java* to the server, I run the following command:

![Image](images/scp_of_file.png)

* I am prompted for my password, but then the file is saved on the server!
* the program `whereami.java` prints the a few properties: the **os** that the program runs on, the **name** of the user, the **home** of the user, and the current **directory**. 
* We can visibly see the difference between running the program on the client side vs. server side. 
client side:
```
Mac OS X
AksharaKuduvalli
/Users/AksharaKuduvalli
/Users/AksharaKuduvalli/Desktop/JavaProjects/cse15l

```
server side: 
![Image](images/server_whereami.png)

---

## Setting an ssh key














