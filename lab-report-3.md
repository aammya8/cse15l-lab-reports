## Lab Report 3: Copy Whole Directories with `scp -r` ✨ 🖥 📂 🏃‍♀️ 🏃‍ 🏃‍ 💨 🪰  🪰 📂 🖥 ✨
*A tutorial on how to copy a whole directory from your local machine into your ieng6 account.*   

*The `scp -r` command asks SSH to copy all the files in your local directory recursively (so it will copy all files and directories inside the directory that is being copied). In this tutorial, the example directory that will be copied to the remote server via SSH is named markdown-parse*  
 
>`System.out.println("Start 🎬")`    

\\( ͡❛ ₒ ͡❛)/ <br/><br/><br/>
   
**PART 1: COPYING A DIRECTORY TO A REMOTE SERVER USING SSH**

There are a few different syntax to use the `scp -r` command.  To copy over everything in your local directory (not just all the files you see with `ls' but all the files in `.git' as well), use the following syntax, with your CSE15L account username in place of USERNAME, and the name of the directory you want to copy in place of DIRECTORY_NAME:      
 

`scp -r . USERNAME@ieng6.ucsd.edu:~/DIRECTORY_NAME`   
 
 
In the command above, `-r` tells `scp` to copy recursively. The `.` is the source  (the current directory). The `~/DIRECTORY_NAME` tells `scp` to create a directory called DIRECTORY_NAME on the remote server, and then copy the contents of the current source directory recursively there. Note that if a directory called DIRECTORY_NAME already exists on the remote server, this `scp` command will overwrite that directory.   

If you want to have more control over which files you want to copy to the remote server, you can also use the following syntax, where FILE_EXTENSION is the type of files you want to copy over (e.g. `java`, `txt`, `md`, etc), and SUBDIRECTORY is the name of the subdirectory you want to copy. Note than neither of these filters are mandatory fields, and you can also add as many file extensions and subdirectories as you want (space-seperated):      
 

`scp -r *.FILE_EXTENSION SUBDIRECTORY USERNAME@ieng6.ucsd.edu:REMOTE_DIRECTORY_NAME`   
 
 
An example of this syntax that we will see later in this tutorial is `scp -r *.java *.md lib/ cs15lwi22@ieng6.ucsd.edu:markdown-parse`. This will copy all java (`.java`) and markdown (`.md`) files in the current directory, along with the `lib` subdirectory, into the directory called `markdown-parse` on the remote server. Note that a directory called markdown-parse must already exist on the remote server for this to work. This syntax does not create any new directories on the remote server. It only copies the specified contents of the current directory into the directory (that already exists on the remote server) called REMOTE_DIRECTORY_NAME. (So if you don't have a directory called REMOTE_DIRECTORY_NAME in the remote server you will get an error).    

![Image](https://user-images.githubusercontent.com/79061216/153681078-538a640f-da4a-4634-a169-cd484ea54eeb.png)          
>`System.out.println("End of Part #1 Description.");`  
 
<br/><br/><br/><br/>



**PART 2: COMPILING AND RUNNING JUNIT TESTS ON REMOTE SERVER**

For reference, the markdown-parse directory contains the following files. The `lib` subdirectory contains the files `hamcrest-core-1.3.jar` and `junit-4.13.2.jar`:   
```   
lib
MarkdownParse.java	
MarkdownParseTest.java
test-file.md
test-file2.md
test-file3.md
test-file4.md
test-file5.md
test-file6.md
test-file7.md
test-file8.md
test-file-a.md		
test-file-b.md
test-file-c.md   
```   

![Image](https://user-images.githubusercontent.com/79061216/153681777-22440463-2502-4e0b-90f8-3dff8410b0da.png)          
>`System.out.println("End of Part #2 Description.");`  
 
<br/><br/><br/><br/>



**PART 3: COPY A WHOLE DIRECTORY AND RUN TESTS IN ONE LINE**

The combined commands for the markdown-parse directory example in this tutorial would be in the following format:   
```   
scp -r *.java *.md lib/ cs15lwi22amt@ieng6.ucsd.edu:markdown-parse; ssh cs15lwi22amt@ieng6.ucsd.edu "cd markdown-parse; javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"   
```   
However, if this gives you an error because the Java version on the remote server is different from the Java version on your machine, replace `javac` in the command above with `/software/CSE/oracle-java-se-14/jdk-14.0.2/bin/javac`, and replace `java` with `/software/CSE/oracle-java-se-14/jdk-14.0.2/bin/java`. The modified command then looks like this:   
```   
scp -r *.java *.md lib/ cs15lwi22amt@ieng6.ucsd.edu:markdown-parse; ssh cs15lwi22amt@ieng6.ucsd.edu "cd markdown-parse; /software/CSE/oracle-java-se-14/jdk-14.0.2/bin/javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; /software/CSE/oracle-java-se-14/jdk-14.0.2/bin/java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"   
```   

![Image](https://user-images.githubusercontent.com/79061216/153683898-17eea0fc-b608-4299-84a0-ba28bb1d21c5.png)          
>`System.out.println("End of Part #3 Description.");`  
 
<br/><br/><br/>

 
>`System.out.println("🎬 End.")`    

\\( ͡╥ ͜ʖ ͡╥)/ 

>`System.out.println("Finished.")`

( ͡⊗ ͜ʖ ͡⊗) <br/><br/>

