
## Lab Report 1: Remote Access 🚗 💨💨💨 
*Tutorial for incoming 15L students on how to log into a course-specific account on ieng6. SSH stands for Secure Shell and it is a network protocol that lets two computers communicate and transfer data/information securely.*  
 
>`System.out.println("Take 1. aCtiON 🎬")`    

\\( ͡❛ ₒ ͡❛)/ <br/><br/>
   
**STEP 1:  INSTALLING 😗🤌VISUAL STUDIO CODE😗🤌**

Go to the Visual Studio Code [website](https://code.visualstudio.com/) and download VS Code. VS Code works with macOS, Windows, and Linux (if you don't have one of those you should not be trying to do this right now 🗿). The download button in the center of the website is for your computer's OS. If you want to download VS Code for another OS, click the down arrow to the right of the download button for more options. Once the download is complete, open the installer and follow the instructions to finish installing VS Code on your device. If you have a Mac, make sure to move Visual Studio Code from the Downloads folder to the Applications folder. When you open VS Code it should look like this:

![Image](https://user-images.githubusercontent.com/79061216/149404740-201fe7fe-f7e6-435d-a5e8-fc8e390ebb32.png)     
>`System.out.println("End of Step 1.");`  
 
<br/><br/>




**STEP 2:  REMOTELY 👉👈CONNECTING👉👈**      

UCSD CSE courses use course-specific accounts SSH accounts. You can look up your account username [here](https://sdacs.ucsd.edu/~icc/index.php). The password is your UCSD SSO password. UCSD passwords do need to be reset at the beginning of each quarter, so make sure to reset your password at the highly-responsive, user-friendly global password reset site 🛩💣💥 (which is linked on the account lookup page once you find your username).    

If you are a Windows user, you will need to [install OpenSHH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse). If you are a macOS or Linux user, you don't need to download any additional software. Now, open a terminal in Visual Studio Code and enter the following command, with your CSE15L account name replacing USERNAME:      
 

`$ ssh USERNAME@ieng6.ucsd.edu`   
 
 
If this is your first time remotely connecting to this server, you will get a message asking if you trust the host and want to continue connecting. Respond to the prompt with `yes` and hit the return key. Finally, enter your UCSD SSO password when prompted for a password. Now you are connected to the server. Once logged in, your terminal should look something like this:

![Image](https://user-images.githubusercontent.com/79061216/149567297-544c1900-8ef7-4356-a30e-70833c283526.png)     
>`System.out.println("End of Step 2.");`  
 
<br/><br/>


**STEP 3:  TRYING SOME 🗣COMMANDS🗣**      

Once connected to the server, you can try out come linux commands. A list of common commands can be found [here](https://linuxconfig.org/linux-commands-cheat-sheet). If you are using Linux or a macOS, you can also try the linux commands on your own device (the client). To do this, first disconnect from the server by typing `exit` into the terminal and pressing enter. Then test out the commands. 

![Image](https://user-images.githubusercontent.com/79061216/149579843-ce8bddcb-133e-42c8-bafd-5017dfcec48d.png)    

![Image](https://user-images.githubusercontent.com/79061216/149579938-e1e77a12-6127-4929-835b-cad64f4671b4.png)     
>`System.out.println("End of Step 3.");`  
 
<br/><br/>


**STEP 4:  🛫MOVING🛩 FILES WITH** ✨`scp`✨      

To copy one or more files from your local computer to the remote computer, you can use the `scp` command, with the file you want to copy in place of FILENAME.FILE_EXTENSION, and your CSE15L account username in place of USERNAME:      
 

`ssh FILENAME.FILE_EXTENSION USERNAME@ieng6.ucsd.edu:~/`   
 
 
Below an example is shown with a file called WhereAmI.java, that prints out properties about the currently connected computer. Note that if you try to copy over a file that already exists in the server, this command will overwrite it. Also note that the scp command does NOT log you into the remote computer. You must use the ssh command to do this.

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

![Image](https://user-images.githubusercontent.com/79061216/149579673-fd107e53-bc28-41c1-92bd-aa039beeaf8c.png)     
>`System.out.println("End of Step 4.");`  
 
<br/><br/>


**STEP 5:  SETTING AN SSH 🔑KEY🔑🏦**      

To log in to the remote computer without typing in your password every time, you can create an SSH key. How SSH keys work is a program called ssh-keygen creates a pair of 2 files—a public key and a private key. Once generating these keys, you copy the public key to the server and keep the private key on the client. Then, the ssh command can pair the private and public keys and use that instead of your password.    

On the client (your local computer), enter the following command in terminal:      
 

`$ ssh-keygen`   
 
 
It will then prompt you to "Enter file in which to save the key (SUGGESTED_FILE_LOCATION)". Here, type the SUGGESTED_FILE_LOCATION into the terminal and press enter. Then it will ask you to enter a passphrase for your SSH key if you want one. 🚨DO NOT MAKE A PASSPRHASE,, JUST PRESS THE ENTER KEY🙇‍♀️🚨 If you have a passphrase for your SSH key, then when trying to ssh later, you won't need to enter your password, but you WILL need to enter a passphrase (defeating the entire purpose of setting an SSH key so that you can connect without a password 🗿). Press enter again when it asks you to confirm your passphrase and then your SSH key has been set. To try logging in using your key, type in the ssh command into the terminal. 

![Image](https://user-images.githubusercontent.com/79061216/149578458-7bd71d7e-5bb2-4622-80b2-c9a21346a947.png)     
>`System.out.println("End of Step 5.");`  
 
<br/><br/>


**STEP 6:  💰OPTIMIZING💰 REMOTE RUNNING**      

There are some shortcuts that can make running commands on both the remote computer and local computer faster:   
* When typing in a the name of a file or directory, press the 'tab' key to complete the name of the file
* Use the upward arrow key on your keyboard to browse previous commands.
* You can write a linux command in double quotes at the end of an ssh command to run it on the remote server directly after connecting.
* You can use semicolons to write and run more than one command on the same line. 🚨If you are trying to run multiple commands on the SERVER at the end of an ssh command, you need to put ALL the commands inside the DOUBLE QUOTES.🚨 If you only put the first command in double quotes then only the first command will run on the remote computer and all successive commands will run on the client (local computer).
