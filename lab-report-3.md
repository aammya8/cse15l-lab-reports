## Lab Report 3: Copy Whole Directories with `scp -r` ✨ 🖥 📂 🏃‍♀️ 🏃‍ 🏃‍ 💨 🪰  🪰 📂 🖥 ✨
*A tutorial on how to copy a whole directory from your local machine into your ieng6 account.*   

*The `scp -r` command asks SSH to copy all the files in your local directory recursively (so it will copy all files and directories inside the directory that is being copied). In this tutorial, the example directory that will be copied to the remote server via SSH is named markdown-parse*  
 
>`System.out.println("Start 🎬")`    

\\( ͡❛ ₒ ͡❛)/ <br/><br/><br/>
   
**PART 1: COPYING A DIRECTORY TO A REMOTE SERVER USING SSH**

There are a few different syntax to use the `scp -r` command.  To copy over everything in your local directory (not just all the files you see with `ls' but all the files in `.git' as well), use the following syntax, with your CSE15L account username in place of USERNAME, and the name of the directory you want to copy in place of DIRECTORY_NAME:      
 

`scp -r . USERNAME@ieng6.ucsd.edu:~/DIRECTORY_NAME`   
