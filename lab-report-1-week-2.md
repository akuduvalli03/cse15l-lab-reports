# Lab Report Week 2: Loggings into an account on ieng6 

## Installing VSCode 

![Image](images/vscode_open.png)
* VSCode is a code editor that will make you life easier. Install VScode [here](https://code.visualstudio.com/). 
* Once you download VSCode, open VSCode. The open page should look something like the image above. 

---

## Remotely connecting to the server
* Open a new terminal window in VSCode. Since I am on a mac, I dont have to download ssh, but windows users can over [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse).
* To find your account for whichever course, search your username [here](https://sdacs.ucsd.edu/~icc/index.php). You may have to change your password to activate the account; I know I did. It might take a while to get activated. 
* After activating your account for a given course, enter ssh [your account] to connect to the ieng6 server remotely. 
```
$ ssh cse15lwi22aaw@ieng6.ucsd.edu
```
* follow the prompts (answer yes) and then you will be promted to enter in you password. It is you ucsd login password. 
* You output should be similar to this image--if so, you have connected to the server!
![Image](images/sshworking.png)

---

