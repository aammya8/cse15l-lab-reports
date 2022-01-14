
## Lab Report 1: Remote Access 🚗 💨💨💨 
*Tutorial for incoming 15L students on how to log into a course-specific account on ieng6. SSH stands for Secure Shell and it is a network protocol that lets two computers communicate and transfer data/information securely.*  
 
`System.out.println("Take 1.🎬")`

**STEP 1:  INSTALLING 😗🤌VISUAL STUDIO CODE😗🤌**

Go to the Visual Studio Code [website](https://code.visualstudio.com/) and download VS Code. VS Code works with macOS, Windows, and Linux (if you don't have one of those you should not be trying to do this right now 🗿). The download button in the center of the website is for your computer's OS. If you want to download VS Code for another OS, click the down arrow to the right of the download button for more options. Once the download is complete, open the installer and follow the instructions to finish installing VS Code on your device. If you have a Mac, make sure to move Visual Studio Code from the Downloads folder to the Applications folder. When you open VS Code it should look like this:

![Image](https://user-images.githubusercontent.com/79061216/149404740-201fe7fe-f7e6-435d-a5e8-fc8e390ebb32.png)     
`System.out.println("End of Step 1.");`  
 
<br/><br/>
     
    

     
     

**STEP 2:  REMOTELY 👉👈CONNECTING👉👈**      

UCSD CSE courses use course-specific accounts SSH accounts. You can look up your account username [here](https://sdacs.ucsd.edu/~icc/index.php). The password is your UCSD SSO password. UCSD passwords do need to be reset at the beginning of each quarter, so make sure to reset your password at the highly-responsive, user-friendly global password reset site 🛩💣💥 (which is linked on the account lookup page once you find your username).    

If you are a Windows user, you will need to [install OpenSHH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse). If you are a macOS or Linux user, you don't need to download any additional software. Now, open a terminal in Visual Studio Code and enter the following command, with your CSE15L account name replacing USERNAME:     $~$
`$ ssh USERNAME@ieng6.ucsd.edu`   
If this is your first time remotely connecting to this server, you will get a message asking if you trust the host and want to continue connecting. Respond to the prompt with `yes` and hit the return key. Finally, enter your UCSD SSO password when prompted for a password. Now you are connected to the server. Once logged in, your terminal should look something like this:    
![Image](https://user-images.githubusercontent.com/79061216/149567297-544c1900-8ef7-4356-a30e-70833c283526.png)     
`System.out.println("End of Step 2.");`  
 
<br/><br/>


**STEP 3:  TRYING SOME 🗣COMMANDS🗣**      

Once connected to the server, you can try out come linux commands. A list of common commands can be found [here](https://linuxconfig.org/linux-commands-cheat-sheet). If you are using Linux or a macOS, you can also try the linux commands on your own device (the client). To do this, first disconnect from the server by typing `exit` into the terminal and pressing enter. Then test out the commands. 

![Image] 

**STEP 4:  🛫MOVING🛩 FILES WITH** ✨`scp`✨      

To copy one or more files from your local computer to the remote computer, you can use the `scp` command.

**STEP 5:  SETTING AN SSH 🔑KEY🔑🏦**      

To log in to the remote computer without typing in your password every time, you can create an SSH key. 

**STEP 6:  💰OPTIMIZING💰 REMOTE RUNNING**      

There are some shortcuts that can make running commands on both the remote computer and local computer faster:   
* When typing in a the name of a file or directory, press the 'tab' key to complete the name of the file
* Use the upward arrow key on your keyboard to browse previous commands.
* You can write a linux command in double quotes at the end of an ssh command to run it on the remote server directly after connecting.
* You can use semicolons to write and run more than one command on the same line. 🚨If you are trying to run multiple commands on the SERVER at the end of an ssh command, you need to put ALL the commands inside the DOUBLE QUOTES.🚨 If you only put the first command in double quotes then only the first command will run on the remote computer and all successive commands will run on the client (local computer).
