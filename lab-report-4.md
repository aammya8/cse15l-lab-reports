## Lab Report 4
*For each snippet of code, add a test to both your implementation of markdown-parse and the implementation you reviewed. Run the tests and show the results of running the tests on each. This means you should add a total of 6 test methods (3 to each implementation).*    

*For each snippet below, you will find a description of the expected output, the code for the test, and the output for running the test on both implementation. There will then be a short explaination of if/how errors with tests for the 3 snippets can be fixed with a small change*  

*Note, to get the expected output, I uploaded the snippets to GitHub as markdown file. I then saw which was links since they were colored blue in the preview. I then figured out what the link inside should be by clicking the blue links. e.g. I put the snippet files into a repo called `random`. Then when I clicked a link it redirected to `https://github.com/doraemon127/random/blob/main/ucsd.edu`, telling me that the read link was `ucsd.edu`*    

**LINKS**

[My repo](https://github.com/doraemon127/markdown-parse)   
[Reviewed repo](https://github.com/CatFish47/markdown-parse) 
 
<br/>  

>`System.out.println("Start.🎙")`    
  
\\( ͡❛ ₒ ͡❛)/ <br/><br/><br/>

   


**SNIPPET 1**

Expected Output: ```[`google.com, google.com, ucsd.edu]```       
 

Code in `MarkdownParseTest.java` for JUnit Test:   
```
    @Test
    public void testSnippet1() throws IOException, NoSuchFileException {
        Path fileName = Path.of("snippet1.md");
        String contents = Files.readString(fileName);
        ArrayList<String> actual_result = MarkdownParse.getLinks(contents);
        List<String> expected_result = new ArrayList<>();
        expected_result.add("`google.com");
        expected_result.add("google.com");
        expected_result.add("ucsd.edu");
        assertEquals(expected_result, actual_result);
    }
```   

 
Output of running test on MY implementation:   
![Image](https://user-images.githubusercontent.com/79061216/155816256-622ddc95-160a-4556-8daf-8458523af271.png)
 

Specific part of JUnit output that shows test failure (if applicable):   
```   
java.lang.AssertionError: expected:<[`google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com, ucsd.edu]>   
```   
 

Output of running test on REVIEWED implementation:   
![Image](https://user-images.githubusercontent.com/79061216/155817464-a6009379-0f0f-4572-8df9-365c5ee075ef.png)      
 

Specific part of JUnit output that shows test failure (if applicable):   
```   
java.lang.AssertionError: expected:<[`google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com, ucsd.edu]>   
```   
 <br/>

Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change:   
* Looking at the output above, my program correctly identified all the actual links, but it also identified `url.com` as a link inside ``` `[a link`](url.com) ```. This is not a correct link format. The ``` ` ``` takes precedence over the `[` since it comes first, so essentially this line of markdown code is `a link` plus the text ](url.com). To fix this, I think an approach would be to check for the opening ``` ` ``` before the `[` and also find out where the closing ``` ` ``` is (e.g. before the `]`, or inside the parentheses, or outside the final closing parentheses). Note that if the entire link format `[link](url)` is within backticks, it does NOT count as a link. When dealing with backticks even beyond this one failed test, however, we also need to consider the situation where the opening backtick is within `[link]` and the closing backtick is after the `)`. In that case, the text inside the parentheses would not be considered a link. Thus, if taking this approach, however, I think it is a more involved change. 

>`System.out.println("End of Snippet #1 Description.");`  
 
<br/><br/><br/><br/>
      
 

**SNIPPET 2**

Expected Output: `[a.com, a.com(()), example.com]`       
 

Code in `MarkdownParseTest.java` for JUnit Test:   
```   
    @Test
    public void testSnippet2() throws IOException, NoSuchFileException {
        Path fileName = Path.of("snippet2.md");
        String contents = Files.readString(fileName);
        ArrayList<String> actual_result = MarkdownParse.getLinks(contents);
        List<String> expected_result = new ArrayList<>();
        expected_result.add("a.com");
        expected_result.add("a.com(())");
        expected_result.add("example.com");
        assertEquals(expected_result, actual_result);
    }
```   
 

Output of running test on MY implementation:   
![Image](https://user-images.githubusercontent.com/79061216/155816383-b8a54436-39ee-443e-b668-d1dc1938e493.png)
 

Specific part of JUnit output that shows test failure (if applicable):   
```   
java.lang.AssertionError: expected:<[a.com, a.com(()), example.com]> but was:<[a.com, b.com, a.com((, example.com]>   
```   
 

Output of running test on REVIEWED implementation:   
![Image](https://user-images.githubusercontent.com/79061216/155817503-22206266-6d3d-40a2-bb4c-c09eb46f0a07.png)      
 

Specific part of JUnit output that shows test failure (if applicable):   
```   
java.lang.AssertionError: expected:<[a.com, a.com(()), example.com]> but was:<[a.com, a.com((, example.com]>   
```   
 <br/>

Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change:   
* Looking at the output above, my program identified `a.com((` as a link inside `[a nested parenthesized url](a.com(()))` instead of the actual link, `a.com(())`. This is because my code stops storing the url string once the first closing parentheses `)` appears. Since in this specific test case, the parentheses are in pairs (there's an outer pair and inner pair in the url, plus the actual outer outer parentheses holding the url), an approach could be to go to the last closing parentheses `)` and work backwards to find the pairs, and everything inside the outer outer parentheses in the `[link](url)` format is stored as the url. I think this change could be made within <10 lines. However, if we consider the situation where the parentheses are not in pairs, it could possibly be a more involved change since you need to figure out where the last parentheses in `[link](url)` is without storing any irrelevant text in the `url` (e.g. if you accidentally skip the closing parentheses and find a later `)`, that would lead to an incorrect link. To make this change shorter, you could add a check for spaces ` ` inside the `url` of `[link](url)` and stop storing the link once a space between the `url` string and `)` is found.
         
>`System.out.println("End of Snippet #2 Description.");`  
 
<br/><br/><br/><br/>

**SNIPPET 3**

Expected Output: `[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]`      
 

Code in `MarkdownParseTest.java` for JUnit Test:   
```
    @Test
    public void testSnippet3() throws IOException, NoSuchFileException {
        Path fileName = Path.of("snippet3.md");
        String contents = Files.readString(fileName);
        ArrayList<String> actual_result = MarkdownParse.getLinks(contents);
        List<String> expected_result = new ArrayList<>();
        expected_result.add("https://www.twitter.com");
        expected_result.add("https://ucsd-cse15l-w22.github.io/");
        expected_result.add("https://cse.ucsd.edu/");
        assertEquals(expected_result, actual_result);
    }
```   

 
Output of running test on MY implementation:   
![Image](https://user-images.githubusercontent.com/79061216/155816431-753e638b-85a7-4627-b8ee-ad3b8e7e50e1.png)
 

Specific part of JUnit output that shows test failure (if applicable):   
```   
java.lang.AssertionError: expected:<[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]> but was:<[
    https://www.twitter.com
, 
    https://ucsd-cse15l-w22.github.io/
, github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



]>   
```   
 

Output of running test on REVIEWED implementation:   
![Image](https://user-images.githubusercontent.com/79061216/155817528-92eedafb-9742-4627-9d67-cc00430a9b85.png)      
 

Specific part of JUnit output that shows test failure (if applicable):   
```   
java.lang.AssertionError: expected:<[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]> but was:<[]>   
```   
 <br/>

Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change:   
* Looking at the output above, my program incorrectly assumes that the `url` string begins immediately after the `(` and that the `url` string ends immediately before the `)`. Thus, my program included the surrounding spaces in the "urls" for `https://www.twitter.com` and `https://ucsd-cse15l-w22.github.io/`. I think this can be fixed with a small (<10 line) change by adding checks for spaces (since they are invalid characters in any url). Looking at the output above, however, my program also incorrectly identified   
```github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



```   
* as a single link, where in reality the only link there is `https://cse.ucsd.edu/` and `github.com` should NOT be counted as a link. This is because my program doesn't stop storing a url string until a closing parentheses is found. I think, for this specific test case where the two "links" are seperated by new lines, it's a small (<10 lines) change. In addition to the check for spaces above, another condition (similar to the spaces check) should be added to check for the `\n`.

          
>`System.out.println("End of Snippet #3 Description.");`  
 
<br/><br/><br/>

 
>`System.out.println("The End. 🎙")`    

\\( ͡╥ ͜ʖ ͡╥)/ 

( ͡⊗ ͜ʖ ͡⊗) <br/><br/>
 
<br/><br/><br/><br/>
     
 


