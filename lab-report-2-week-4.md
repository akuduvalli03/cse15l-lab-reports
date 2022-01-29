# Lab Report Week 4: Debugging

## Error 1: Links using only parentheses

![Image](images/onlyparen.png)
* The test file that prompted me to make this change was [this file](testcase1.md) where the label for the link also used parentheses instead of open and close brackets. 

* the output without fixing the mistake looks like this (when it fails):
![Image](images/infiniteloop.png)
* As shown above, without fixing the error, the original program would result in an infinite loop. This is the *symptom* of the failure inducing input, but it is not the source of the issue. 

* The **bug** is that the original program immediately looks for an open and close bracket, because it expects that the format of every link will be like `[file label](link.com)` which, as shown by the failure inducing input, is not always the case. The symptom, the infinite loop, is a result of the fact that in this part of the while loop, 
```java
int nextOpenBracket = markdown.indexOf("[", currentIndex);
int nextCloseBracket = markdown.indexOf("]", nextOpenBracket);
```
* the values of `nextOpenBracket` and `nextCloseBracket` will both be -1, and current index will not increment properly as a result, causing an infinite loop. This is the **bug**. 

* In my solution for this error, 
```java
markdown = markdown.replace("\n(","\n[");
markdown = markdown.replace(")(","](");
```
* I replaced the open parentheses at the beginning with a bracket, and close parentheses at the end with a close bracket, to ensure that the rest of the program runs successfully. 
