
## Lab Report 1: Remote Access 🚗 💨💨💨 
Tutorial for incoming 15L students on how to log into a course-specific account on ieng6.

---

**STEP 1:  INSTALLING 😗🤌VISUAL STUDIO CODE😗🤌**

Go to the Visual Studio Code [website](https://code.visualstudio.com/) and download VS Code. VS Code works with macOS, Windows, and Linux (if you don't have one of those you should not be trying to do this right now 🗿). The download button in the center of the website is for your computer's OS. If you want to download VS Code for another OS, click the down arrow to the right of the download button for more options. Once the download is complete, open the installer and follow the instructions to finish installing VS Code on your device. If you have a Mac, make sure to move Visual Studio Code from the Downloads folder to the Applications folder. When you open VS Code it should look like this:

![Image](https://user-images.githubusercontent.com/79061216/149404740-201fe7fe-f7e6-435d-a5e8-fc8e390ebb32.png)     

     
     

**STEP 2:  REMOTELY 👉👈CONNECTING👉👈**      

UCSD CSE courses use course-specific accounts SSH accounts. You can look up your account username [here](https://sdacs.ucsd.edu/~icc/index.php). The password is your UCSD SSO password. UCSD passwords do need to be reset at the beginning of each quarter, so make sure to reset your password at the highly-responsive, user-friendly global password reset site 🛩💣💥 (which is linked on the account lookup page once you find your username).    

If you are a Windows user, you will need to [install OpenSHH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse). If you are a macOS or Linux user, you don't need to download any additional software. Now, open a terminal in Visual Studio Code and enter the following command, with your CSE15L account name replacing USERNAME:     
`$ ssh USERNAME@ieng6.ucsd.edu`   
If this is your first time remotely connecting to this server, you will get a message asking if you trust the host and want to continue connecting. Respond to the prompt with `yes` and hit the return key. Finally, enter your UCSD SSO password when prompted for a password.


**STEP 3:  TRYING SOME 🗣COMMANDS🗣**

**STEP 4:  🛫MOVING🛩 FILES WITH** ✨`scp`✨

**STEP 5:  SETTING AN SSH 🔑KEY🔑🏦**

**STEP 6:  💰OPTIMIZING💰 REMOTE RUNNING**
