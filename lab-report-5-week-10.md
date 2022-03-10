# Lab Report 5

I ended up finding tests with different results from the two different implementations of MarkDownParse.java by running a bash for loop with all the test files on both implementations of the parser. In order to tell which output corresponded with which test, I added a print statement in the main method of the MarkdownParse class for both implementations that specifies which test file is being tested before printing the output. After running these bash for loops, the results for both my implementation and the provided implementation were printed in 2 seperate .txt files. Here is a snippet of what the resulting text files looked like:

![Image](/img/lab-report-5/results-snippet.png)

From here, all I had to do was look through both of the resulting .txt files for each implementation and see which outputs were different for some 2 tests. 

<br/>

---
<br/>

## Test 1

The first test that I chose that provided different results in the two implementations was test file 504. The contents of this test file are shown below:

![Image](/img/lab-report-5/test-504-contents.png)

The CommonMark demo site shows us that the test file produces the following output:

![Image](/img/lab-report-5/test-504-commonmark-demo.png)

This means the expected output for a correct implementation of MarkDownParse for this test would be:

`test-files/504.md[/url, /url, /url]`

The output for the provided implementation of MarkDownParse was:

![Image](/img/lab-report-5/test-504-class-impl-output.png)

The output for my implementation of MarkDownParse was:

![Image](/img/lab-report-5/test-504-my-impl-output.png)

Both implementations of the MarkDownParse class seem to be incorrect for this test, after comparing the actual outputs to the expected output.

Specifically looking at my own implementation of MarkDownParse.java, the issue seems to be stemming from the code counting the text after the space in the link as part of the actual link, when it should not. The relevant code for this issue is located in the getLinks method of the MarkDownParse class.

![Image](/img/lab-report-5/test-504-relevant-code.png)

The issue with this code is that it does not account for any spaces within the links it is parsing for. The only indexes it looks for are parentheses and brackets. 

<br/>

---
<br/>

## Test 2

The second test that I chose that provided different results in the two implementations was test file 504. The contents of this test file are shown below:

![Image](/img/lab-report-5/test-488-contents.png)

The CommonMark demo site shows us that the test file produces the following output:

![Image](/img/lab-report-5/test-488-commonmark-demo.png)

This means the expected output for a correct implementation of MarkDownParse for this test would be:

`test-files/488.md[/my uri]`

The output for the provided implementation of MarkDownParse was:

![Image](/img/lab-report-5/test-488-class-impl-output.png)

The output for my implementation of MarkDownParse was:

![Image](/img/lab-report-5/test-488-my-impl-output.png)

Both implementations of the MarkDownParse class seem to be incorrect for this test, after comparing the actual outputs to the expected output.

Specifically looking at the provided implementation of MarkdownParse.java, the issue with this test seems to be stemming from the fact that the code does not recognize links within angular brackets as valid links, when it should. The relevant code that pertains to this issue is located within the getLinks method of the MarkDownParse class, as shown below 

![Image](/img/lab-report-5/test-488-relevant-code.png)

The issue with this code is that it does not look for angular brackets at all, much less the contents within them. A potential fix for this issue would be creating a pointer to any angular brackets within the link and counting the contents within them as valid links.