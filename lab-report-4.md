## Lab Report 4
*For each snippet of code, add a test to both your implementation of markdown-parse and the implementation you reviewed. Run the tests and show the results of running the tests on each. This means you should add a total of 6 test methods (3 to each implementation).*    

*For each snippet below, you will find a description of the expected output, the code for the test, and the output for running the test on both implementation. There will then be a short explaination of if/how errors with tests for the 3 snippets can be fixed with a small change*  

*Note, to get the expected output, I uploaded the snippets to GitHub as markdown file. I then saw which was links since they were colored blue in the preview. I then figured out what the link inside should be by clicking the blue links. e.g. I put the snippet files into a repo called `random`. Then when I clicked a link it redirected to `https://github.com/doraemon127/random/blob/main/ucsd.edu`, telling me that the read link was `ucsd.edu`*    

>`System.out.println("Start.🎙")`    

\\( ͡❛ ₒ ͡❛)/ <br/><br/><br/>


**LINKS**

[My repo](https://github.com/doraemon127/markdown-parse)   
[Reviewed repo](https://github.com/CatFish47/markdown-parse) 
 
<br/><br/>
   


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
 

Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change:          
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
 

Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change:          
>`System.out.println("End of Snippet #3 Description.");`  
 
<br/><br/><br/>

 
>`System.out.println("The End. 🎙")`    

\\( ͡╥ ͜ʖ ͡╥)/ 

( ͡⊗ ͜ʖ ͡⊗) <br/><br/>
 
<br/><br/><br/><br/>
     
 


