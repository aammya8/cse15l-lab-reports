## Lab Report 5
*For this lab report, choose any two tests from the 652 commonmark-spec tests where your implementation (or a representative implementation from your group) had different answers than the implementation we provided for lab 9. Note that this is the implementation in the markdown-parse repository, not the one you did today in lab 10. The tests with different answers should correspond to different bugs – that is, you couldn’t easily fix both with one code change*    
<br/>  
>`System.out.println("Start.🎙")`    
  
\\( ͡❛ ₒ ͡❛)/ <br/><br/><br/>

   


**🤓🤓🤓🤓🤓  TEST 1  🤓🤓🤓🤓🤓**

*Test file*: 194.md      
``` 
[Foo*bar\]]:my_(url) 'title (with parens)'

[Foo*bar\]]
```   
*Expected output*: ```[]```   
*Output of my implementation*: ```[]```   
*Output of provided implementation*: ```[url]```   

*How I found different result*: 
* Put results from my implementation and provided implementation into seperate `txt` files and used `diff`   

*Correct implementation*:   
* Based on the expected and actual outputs above, my implementation is correct. The provided implementation INCORRECTLY identifies ```[url]``` as a link.  

*Bug in incorrect implementation*:   
* To find the bug in the provided implementation, we need to look at the `getLinks` method with the method signature ```public static ArrayList<String> getLinks(String markdown) {}```. If we look at the contents of the test file above, we can see that `url` should not be identified as a link because (1) there's superfluous text (`:my_`) between the closing bracket `]` and the opening parentheses `(`     
 
*Code in incorrect implementation that should be fixed*:   
```   
   
```  
 

>`System.out.println("End of Test #1 Description.");`  
 
<br/><br/><br/><br/>

**🚨🚨🚨🚨🚨  TEST 2  🚨🚨🚨🚨🚨**

*Test file*:      
``` 
   
```   
*Expected output*:    
*Output of my implementation*:   
*Output of provided implementation*:   

*How I found different result*: 
* Put results from my implementation and provided implementation into seperate `txt` files and used `diff`   

*Correct implementation*:   
* Add text here  

*Bug in incorrect implementation*:   
* Add text here    
 
*Code in incorrect implementation that should be fixed*:   
```   
   
```  
 

>`System.out.println("End of Test #2 Description.");`  
 
<br/><br/><br/>

 
>`System.out.println("The End. 🎙")`    

\\( ͡╥ ͜ʖ ͡╥)/ 

( ͡⊗ ͜ʖ ͡⊗) <br/><br/>
 
<br/><br/><br/><br/>
     
 

