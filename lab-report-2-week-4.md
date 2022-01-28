# Lab Report 2

## Issue 1

The first issue our group attempted to fix was when a link was given in just parentheses, without the brackets preceding it, as given below.

>`(link.com)`

Here is the code change diff from Github for this fix:

![Image](/img/Issue-1-Fix-ss.png)

[Here is the link to the test file of a failure-inducing input that prompted us to make this change](https://github.com/anishcd/markdown-parse/blob/15f78b4aadaf54f9d4ded2c8a9433b1111b760ab/test-issue-1.md)

After running this test file on the initial version of MarkdownParse.java (before any bug fixes were made), this is the output from the terminal:

![Image](/img/Issue-1-Run-Initial-MarkdownParse.png)

Although the link in this test file is supposed to be considered invalid as it is not preceded by a set of square brackets (``[]``), the initial version of the MarkdownParse.java file considers it a valid link. The failure-inducing input, which is the text in parantheses, reveals the bug in the code, which occurs since the code considers any set of parantheses to be a valid link. The symptom that we see results in the output from the terminal when the code is run with this test file, as the link is considered valid, and is added to the list of valid links, when it is not supposed to be.

<br/>

---
<br/>

## Issue 2

The second issue our group attempted to fix was when the parantheses to a link were left open at the end, as shown below.

```[invalid link](not a url```

Here is the code change diff from Github for this fix:

![Image](/img/Issue-1-Fix-ss.png)

[Here is the link to the test file of a failure-inducing input that prompted us to make this change](https://github.com/anishcd/markdown-parse/blob/15f78b4aadaf54f9d4ded2c8a9433b1111b760ab/test-issue-2.md)

After running this test file on the initial version of MarkdownParse.java before any bug fixes were made, this was the output from the terminal:

![Image](/img/Issue-2-Run-Init-MarkdownParse.png)

The bug in this scenario exists in the code, which looks for the closing paranthis after seeing an instance of an open paranthesis. In the test file, however, or the failure-inducing input, the file does not contain a closing parenthesis, making the link invalid. As a result, we see the symptom of the bug through the output after running the code, which throws a StringIndexOutOfBoundsException, since the index for the closing parenthesis is -1, as it does not exist.

<br/>

---
<br/>

## Issue 3

The third issue our group attempted to fix was when there existed some text betweeen the square brackets and the parentheses when creating a link, as shown below.

```[Here is a link] and some text (url.com)```

Here is the code change diff from Github for this fix:

![Image](/img/Issue-2-Fix-ss.png)

[Here is the link to the test file of a failure-inducing input that prompted us to make this change](https://github.com/anishcd/markdown-parse/blob/15f78b4aadaf54f9d4ded2c8a9433b1111b760ab/test-issue-3.md)

After running this test file on the initial version of MarkdownParse.java before any bug fixes were made, this was the output from the terminal:

![Image](/img/Issue-3-Run-Pre-Bug-Fix.png)

The bug in this scenario comes from the code, which only looks for the first and last instances of square brackets and parentheses in a line. If these criteria are met, then the text is considered a valid link. In the failure-inducing input, the text between the brackets and parentheses causes the link to be invalid, but the symptom of the bug shows that that code still consideres it a valid link format. 


