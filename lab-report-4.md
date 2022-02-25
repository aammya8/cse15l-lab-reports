## Lab Report 4
*For each snippet of code, add a test to both your implementation of markdown-parse and the implementation you reviewed. Run the tests and show the results of running the tests on each. This means you should add a total of 6 test methods (3 to each implementation).*   

*Note, to get the expected output, I uploaded the snippets to GitHub as markdown file. I then saw which was links since they were colored blue in the preview. I then figured out what the link inside should be by clicking the blue links. e.g. I put the snippet files into a repo called `random`. Then when I clicked a link it redirected to `https://github.com/doraemon127/random/blob/main/ucsd.edu`, telling me that the read link was `ucsd.edu`*    

*For each snippet below, you will find a description of the expected output, the code for the test, and the output for running the test on both implementation. There will then be a short explaination of if/how errors with tests for the 3 snippets can be fixed with a small change*  
 
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
 

Specific part of JUnit output that shows test failure (if applicable):      
 

Output of running test on REVIEWED implementation:      
 

Specific part of JUnit output that shows test failure (if applicable):      
 

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
 

Specific part of JUnit output that shows test failure (if applicable):      
 

Output of running test on REVIEWED implementation:      
 

Specific part of JUnit output that shows test failure (if applicable):      
 

Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change:          
>`System.out.println("End of Snippet #2 Description.");`  
 
<br/><br/><br/><br/>

**SNIPPET 3**

Expected Output: `[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]`      
 

Code in `MarkdownParseTest.java` for JUnit Test:      
 

Output of running test on MY implementation:      
 

Specific part of JUnit output that shows test failure (if applicable):      
 

Output of running test on REVIEWED implementation:      
 

Specific part of JUnit output that shows test failure (if applicable):      
 

Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change:          
>`System.out.println("End of Snippet #3 Description.");`  
 
<br/><br/><br/>

 
>`System.out.println("The End. 🎙")`    

\\( ͡╥ ͜ʖ ͡╥)/ 

( ͡⊗ ͜ʖ ͡⊗) <br/><br/>
 
<br/><br/><br/><br/>
     
 


