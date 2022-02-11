## Lab Report 3: Copy Whole Directories with `scp -r` ✨ 🖥 📂 🏃‍♀️ 🏃‍ 🏃‍ 💨 🪰  🪰 📂 🖥 ✨
*A tutorial on how to copy a whole directory from your local machine into your ieng6 account.*   

*The `scp -r` command asks SSH to copy all the files in your local directory recursively (so it will copy all files and directories inside the directory that is being copied). In this tutorial, the example directory that will be copied to the remote server via SSH is named markdown-parse*  
 
>`System.out.println("Start 🎬")`    

\\( ͡❛ ₒ ͡❛)/ <br/><br/><br/>
   
**PART 1: COPYING A DIRECTORY TO A REMOTE SERVER USING SSH**

There are a few different syntax to use the `scp -r` command.  To copy over everything in your local directory (not just all the files you see with `ls' but all the files in `.git' as well), use the following syntax, with your CSE15L account username in place of USERNAME, and the name of the directory you want to copy in place of DIRECTORY_NAME:      
 

`scp -r . USERNAME@ieng6.ucsd.edu:~/DIRECTORY_NAME`   
 
 
In the command above, `-r` tells `scp` to copy recursively. The `.` is the source  (the current directory). The `~/DIRECTORY_NAME` tells `scp` to create a directory called DIRECTORY_NAME on the remote server, and then copy the contents of the current source directory recursively there. Note that if a directory called DIRECTORY_NAME already exists on the remote server, this `scp` command will overwrite that directory.   

If you want to have more control over which files you want to copy to the remote server, you can also use the following syntax, where FILE_EXTENSION is the type of files you want to copy over (e.g. `java`, `txt`, `md`, etc), and SUBDIRECTORY is the name of the subdirectory you want to copy. Note than neither of these filters are mandatory fields:      
 

`scp -r *.FILE_EXTENSION SUBDIRECTORY USERNAME@ieng6.ucsd.edu:REMOTE_DIRECTORY_NAME`   
 
 
An example of this syntax that we will see later in this tutorial is `scp -r *.java *.md lib/ cs15lwi22@ieng6.ucsd.edu:markdown-parse`. This will copy all java (`.java`) and markdown (`.md`) files in the current directory, along with the `lib` subdirectory, into the directory called `markdown-parse` on the remote server. Note that a directory called markdown-parse must already exist on the remote server for this to work. This syntax does not create any new directories on the remote server. It only copies the specified contents of the current directory into the directory (that already exists on the remote server) called REMOTE_DIRECTORY_NAME. (So if you don't have a directory called REMOTE_DIRECTORY_NAME in the remote server you will get an error).    

![Image](https://user-images.githubusercontent.com/79061216/153679655-ae5b46f4-9c49-48df-bcbf-f649b131aa8e.png)          
>`System.out.println("End of Part #1 Description.");`  
 
<br/><br/><br/><br/>



**PART 2: COMPILING AND RUNNING JUNIT TESTS ON REMOTE SERVER**

See below.    

![Image]()          
>`System.out.println("End of Part #2 Description.");`  
 
<br/><br/><br/><br/>



**PART 3: COPY A WHOLE DIRECTORY AND RUN TESTS IN ONE LINE**

See below.    

![Image]()          
>`System.out.println("End of Part #3 Description.");`  
 
<br/><br/><br/>

 
>`System.out.println("🎬 End.")`    

\\( ͡╥ ͜ʖ ͡╥)/ 

>`System.out.println("Finished.")`

( ͡⊗ ͜ʖ ͡⊗) <br/><br/>

