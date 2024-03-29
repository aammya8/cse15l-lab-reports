## Lab Report 5
*For this lab report, choose any two tests from the 652 commonmark-spec tests where your implementation (or a representative implementation from your group) had different answers than the implementation we provided for lab 9. The tests with different answers should correspond to different bugs – that is, you couldn’t easily fix both with one code change*    
<br/>  
>`System.out.println("Start.🎙")`    
  
\\( ͡❛ ₒ ͡❛)/ <br/><br/><br/>

   


**🤓🤓🤓🤓🤓  TEST 1  🤓🤓🤓🤓🤓**

**Test file**: 201.md      
``` 
[foo]: <bar>(baz)

[foo]
```   
**Expected output**: ```[]```   
**Output of my implementation**: ```[]```   
**Output of provided implementation**: ```[baz]```   

**How I found different result**: 
* Ran a bash for loop and put results from my implementation and provided implementation into seperate `txt` files and used `diff`   

**Correct implementation**:   
* Based on the expected and actual outputs above, my implementation is correct. The provided implementation INCORRECTLY identifies ```[baz]``` as a link.  

**Bug in incorrect implementation**:   
* To find the bug in the provided implementation, we need to look at the `getLinks` method with the method signature ```public static ArrayList<String> getLinks(String markdown) {}```. If we look at the contents of the test file above, we can see that `baz` should not be identified as a link because (1) there's superfluous text/space (`: <bar>`) between the closing bracket `]` and the opening parentheses `(`, and (2) `baz` is not an actual valid url. In the current program, as long as the `[`, `]`, `(`, and `)` are all found, the potential link inside the parentheses `()` is added to the ArrayList of links. Below I have copy-pasted the code simply adds the potential link. To improve the program to make it produce the correct output for this test file, to address issue (1) described earlier, the snippet of code below should be surrounded by an if statement that checks whether `openParen = nextCloseBracket + 1`. This addition would check to make sure that the open parentheses is immediately after the close bracket (`](`). As for problem (2), the fact that `baz` isn't even a url, some more forms of link validation should be added to this code. Currently, in the line `if(potentialLink.indexOf(" ") == -1 && potentialLink.indexOf("\n") == -1)` of the code below, the program only checks to make sure that there is no space or newline character before adding the potential link to the ArrayList of links. Something that all links have is a `.`, so another condition should be added to this line of code that checks if `potentialLink.indexOf(".") != -1`. These two changes would make the program produce the correct output for this test case.     
 
**Code in incorrect implementation that should be fixed**:   
```
String potentialLink = markdown.substring(openParen + 1, closeParen).trim();
if(potentialLink.indexOf(" ") == -1 && potentialLink.indexOf("\n") == -1) {
      toReturn.add(potentialLink);
      currentIndex = closeParen + 1;
}    
```  
 

>`System.out.println("End of Test #1 Description.");`  
 
<br/><br/><br/><br/>

**🚨🚨🚨🚨🚨  TEST 2  🚨🚨🚨🚨🚨**

**Test file**: 342.md      
``` 
[not a `link](/foo`)   
```   
**Expected output**: `[]`    
**Output of my implementation**: `[]`   
**Output of provided implementation**: ```[/foo`]```   

**How I found different result**: 
* Ran a bash for loop and put results from my implementation and provided implementation into seperate `txt` files and used `diff`   

**Correct implementation**:   
* Based on the expected and actual outputs above, my implementation is correct. The provided implementation INCORRECTLY identifies ```[/foo`]``` as a link.  

**Bug in incorrect implementation**:   
* To find the bug in the provided implementation, we need to look at the `getLinks` method with the method signature ```public static ArrayList<String> getLinks(String markdown) {}```. If we look at the contents of the test file above, we can see that ``` /foo` ``` should not be identified as a link because in ``[not a `link]`` the opening backtick ``` ` ``` comes before the closing bracket `]`. This means that the backtick (code block) takes precedence over the closing bracket (link format), so it's actualy code wrapped in text:  [not a `link](/foo`). The issue in the program making this specific test case fail is that the program never checks for SINGULAR backticks inside the `[` and `)`. As we can see in the snippet of code below, the program does check for code BLOCKS (indicated by THREE backticks), but it never checks for SINGULAR backticks. Even the code for checking for code blocks is flawed since in the line `if(nextCodeBlock < nextOpenBracket && nextCodeBlock != -1)` the program doesn't consider the possibility of the code block starting after the `nextOpenBracket` but before the `closeParen`. To fix this, a variable called `nextCodeLine` should be added to track singular backticks, and more conditions should be added to an if-statement to `continue` if the `nextCodeLine` and/or `nextCodeBlock` start in between the `nextOpenBracket` and `closeParen` (Note the structure of the code will have to be modified so that `closeParen` is calculated before the new if-statement.
 
**Code in incorrect implementation that should be fixed**:   
```   
int nextOpenBracket = markdown.indexOf("[", currentIndex);
int nextCodeBlock = markdown.indexOf("\n```");
if(nextCodeBlock < nextOpenBracket && nextCodeBlock != -1) {
    int endOfCodeBlock = markdown.indexOf("\n```");
    currentIndex = endOfCodeBlock + 1;
    continue;
}
int nextCloseBracket = markdown.indexOf("]", nextOpenBracket);
int openParen = markdown.indexOf("(", nextCloseBracket);
int closeParen = findCloseParen(markdown, openParen);
```  
 

>`System.out.println("End of Test #2 Description.");`  
 
<br/><br/><br/>

 
>`System.out.println("The End. 🎙")`    

\\( ͡╥ ͜ʖ ͡╥)/ 

( ͡⊗ ͜ʖ ͡⊗) <br/><br/>
 
<br/><br/><br/><br/>
     
 

