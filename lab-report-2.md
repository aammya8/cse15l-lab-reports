
## Lab Report 2: Debugging 💣💥❌🦟🪳🐜🦟🪳🐜❌💥💣 
*Debugging the markdown-parse program.*   

*For each change described below, you will find a link to the test-file for a failure-inducing input that prompted the change, a screenshot of the terminal output of running the file demonstrating the symptom of the failure-inducing input, and a screenshot of the the GitHub commit (showing the changes made).*  
 
>`System.out.println("Attack of the Bugs — Take 1: aCtiON 🎬")`    

\\( ͡❛ ₒ ͡❛)/ <br/><br/><br/>

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
<br/><br/><br/>

   
**CHANGE #1**

*Description of bug,symptom, and improvement*:    
The first test file to cause a failure-inducing input was [test-file2.md](https://github.com/doraemon127/markdown-parse/blob/main/test-file2.md). As seen in the first image below, running the program on test-file2.md led to an infinte loop. (In the getLinks method in MarkdownParse.java, a print statement to print currentIndex was added at the end of the while loop to display infinite loops). If we look at the original code (above), we can see that the value of currentIndex never increases after the last close parentheses ")" in the file. However, to exit the loop, currentIndex has to become >= the length of the file. Therefore, if a ")" is not the last character in the file, there will be an issue of an infinite loop. To fix this issue, the original code has been surrounded by an if-else statement (see second image below for screenshot of changes made in GitHub [commit](https://github.com/doraemon127/markdown-parse/commit/dc56311921a1fca13324f7803f466df738f52edf)).

![Image](https://user-images.githubusercontent.com/79061216/151627499-16484e42-0464-4b4c-a40b-e53890455bb6.png)     


![Image](https://user-images.githubusercontent.com/79061216/151627600-00b614f5-4e77-4c83-b220-55695dadbcb3.png)     
>`System.out.println("End of Change #1 Description.");`  
 
<br/><br/><br/><br/>




**CHANGE #2**

*Description of bug,symptom, and improvement*:    
After making this change, the next file to cause a failure-inducing input was [test-file5.md](https://github.com/doraemon127/markdown-parse/blob/main/test-file5.md). As seen in the first image of terminal output below, the program incorrectly identified "page.com" as a link. Now let's look at the code to understand why this is happening. As we can see, the line `int openParen = markdown.indexOf("(", nextCloseBracket);` does not take into consideration the possibility of there being text between the closing bracket "]" and the opening parentheses "(". To address this issue, the code has been modified as seen in the screenshot of the GitHub [commit](https://github.com/doraemon127/markdown-parse/commit/7faabceaf8ebf6a42e154772228fe6b7ac3217f1) below.

![Image](https://user-images.githubusercontent.com/79061216/151628258-02a96232-8646-4246-95ba-7f5d71238844.png)     


![Image](https://user-images.githubusercontent.com/79061216/151630015-e2ae221e-14cc-4398-841c-c1e7fa8da2cb.png)     
>`System.out.println("End of Change #2 Description.");`  
 
<br/><br/><br/><br/>



**CHANGE #3**

*Description of bug,symptom, and improvement*:    
After making this change, the next file to cause a failure-inducing input was [test-file6.md](https://github.com/doraemon127/markdown-parse/blob/main/test-file6.md). As seen in the first screenshot below of terminal output, the program incorrectly identifies the opening parentheses "(" as part of the link. Looking at the previous code (after Change #2), we can see that in the line `toReturn.add(markdown.substring(start + 1, end));`, instead of adding `1` to `start`, we should not be adding `2`, since the line `int start = markdown.indexOf("](", currentIndex);` makes `start` equal to the index of the "]". The code has been modified to fix this issue, as seen in the screenshot of the GitHub [commit](https://github.com/doraemon127/markdown-parse/commit/4c5971d9addbb3f2058af2da4dccfe2f44f1d88e) below.    

![Image](https://user-images.githubusercontent.com/79061216/151630700-4c0c27ee-6869-4942-8d31-4e040d8dc76e.png)     


![Image](https://user-images.githubusercontent.com/79061216/151632099-03a9ac5a-499b-405c-b67f-ce8b4112d105.png)     
>`System.out.println("End of Change #3 Description.");`  
 
<br/><br/><br/><br/>    


**✨BONUS✨CHANGE #4**

*Description of bug,symptom, and improvement*:    
After making this change, the last file to cause a failure-inducing input was [test-file8.md](https://github.com/doraemon127/markdown-parse/blob/main/test-file8.md). As seen in the first screenshot below of terminal output, the program incorrectly identifies "a link on the first line" as a link. Looking at the previous code (after Change #3), we can see that this is because the code simply identifies any text in the format [](text) as a link. The program currently has no method of confirming whether the text inside the parentheses is a real link. Something that all links have is a ".", so we can add a period to the if-statement. This, of course, is not a fool proof check of whether or not the text inside the parentheses is a link, but it is a start. For a more thorough check, we can add conditions into the if-statement to check if the text contains a domain-name (such as ".com", ".html") and so on. The code has been modified to BEGIN to fix the issue of confirming whether the text REALLY is a link, as seen in the screenshot of the GitHub [commit](https://github.com/doraemon127/markdown-parse/commit/e02a32092dea04ab07e3c74f85aff96a781e3d9d) below.    

![Image](https://user-images.githubusercontent.com/79061216/151632403-99ae952f-55a3-4cc2-a4fa-98ed39cb28b6.png)     


![Image](https://user-images.githubusercontent.com/79061216/151633311-09174e7d-8868-4252-87ec-ee21ee174367.png)     
>`System.out.println("End of Change #4 Description.");`  
 
<br/><br/><br/><br/>



**[FINAL CODE](https://github.com/doraemon127/markdown-parse/blob/main/MarkdownParse.java) LeSs BUg-Y🪳**   
```
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.ArrayList;

public class MarkdownParse {

    public static ArrayList<String> getLinks(String markdown) {
        ArrayList<String> toReturn = new ArrayList<>();
        int currentIndex = 0;
        while(currentIndex < markdown.length()) {
            String remaining = markdown.substring(currentIndex, markdown.length());
            if (remaining.contains("]") && remaining.contains("](") &&
                remaining.contains(")") && remaining.contains(".")) {
                    int start = markdown.indexOf("](", currentIndex);
                    int end = markdown.indexOf(")", start);
                    toReturn.add(markdown.substring(start + 2, end));
                    currentIndex = end + 1;
            }
            else {
                currentIndex = markdown.length();
            }
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

 
>`System.out.println("🎬 End Take 1. Destroy el bugs.🗡🔫")`    

\\( ͡╥ ͜ʖ ͡╥)/ 

>`System.out.println("Eliminate the bugs x_x.")`

( ͡⊗ ͜ʖ ͡⊗) <br/><br/>
 


