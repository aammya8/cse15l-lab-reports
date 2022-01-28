
## Lab Report 2: Debugging 💣💥❌🦟🪳🐜🦟🪳🐜❌💥💣 
*Debugging the markdown-parse program.*   

*For each change described below, you will find a link to the test-file for a failure-inducing input that prompted the cahnge, a screenshot of the terminal output of running the file demonstrating the symptom of the failure-inducing input, and a screenshot of the the GitHub commit (showing the changes made).*  
 
>`System.out.println("Attack of the Bugs — Take 1: aCtiON 🎬")`    

\\( ͡❛ ₒ ͡❛)/ <br/><br/>

**[ORIGINAL CODE](https://github.com/ucsd-cse15l-w22/markdown-parse/blob/main/MarkdownParse.java) veRY BUg-Y🦟🦟🦟**   
```
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.ArrayList;

public class MarkdownParse {
    public static ArrayList<String> getLinks(String markdown) {
        ArrayList<String> toReturn = new ArrayList<>();
        // find the next [, then find the ], then find the (, then take up to
        // the next )
        int currentIndex = 0;
        while(currentIndex < markdown.length()) {
            int nextOpenBracket = markdown.indexOf("[", currentIndex);
            int nextCloseBracket = markdown.indexOf("]", nextOpenBracket);
            int openParen = markdown.indexOf("(", nextCloseBracket);
            int closeParen = markdown.indexOf(")", openParen);
            toReturn.add(markdown.substring(openParen + 1, closeParen));
            currentIndex = closeParen + 1;
        }
        return toReturn;
    }
    public static void main(String[] args) throws IOException {
		Path fileName = Path.of(args[0]);
	    String contents = Files.readString(fileName);
        ArrayList<String> links = getLinks(contents);
        System.out.println(links);
    }
}   
```
<br/><br/>

   
**CHANGE #1**

*Description of bug,symptom, and improvement*:    
The first test file to cause a failure-inducing input was [test-file2.md](https://github.com/doraemon127/markdown-parse/blob/main/test-file2.md). In the getLinks method in MarkdownParse.java, a print statement to print  currentIndex was added at the end of the while loop. As seen in the image below, running the program on test-file2.md led to an infinte loop. If we look at the original code (above), we can see that the value of currentIndex never increases after the last close parentheses ")" in the file. However, to exit the loop, currentIndex has to become >= the length of the file. Therefore, if a ")" is not the last character in the file, there will be an issue of an infinite loop.  

![Image]()     


![Image]()     
>`System.out.println("End of Change #1 Description.");`  
 
<br/><br/>




**CHANGE #2**

*Description of bug,symptom, and improvement*:   

![Image]()     


![Image]()     
>`System.out.println("End of Change #2 Description.");`  
 
<br/><br/>



**CHANGE #3**

*Description of bug,symptom, and improvement*:   

![Image]()     


![Image]()     
>`System.out.println("End of Change #3 Description.");`  
 
<br/><br/>    
 
>`System.out.println("🎬 End Take 1. Destroy el bugs.")`    

\\( ͡╥ ͜ʖ ͡╥)/ 

>`System.out.println("Eliminate the bugs x_x.")`

( ͡⊗ ͜ʖ ͡⊗) <br/><br/>
 


