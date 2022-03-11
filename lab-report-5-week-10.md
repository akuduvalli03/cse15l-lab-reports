# Lab Report Week 5: CommonMark Comparisons

## First test file: `[link](foo\)\:)`

* I made a fresh clone of both the `markdown-parse` repositories from lab 9 and mine onto `ieng6`. I created a file called `test-lab5.txt` in both directories that contained the following:

```md
[link](foo\)\:)
```

* output on the class `markdown-parse`: 

```
[cs15lwi22aaw@ieng6-201]:lab5:103$ java MarkdownParse test-lab5.txt
[foo\]
```

* output on my markdown-parse: 

``` 
[cs15lwi22aaw@ieng6-201]:lab5mi:127$ java MarkdownParse3 test-lab5.txt
[]
```

* I didn't use `diff` or anything to find the difference between the two outputs because the differences are kind of obvious. 

* I think that neither implementation is correct because on the **commonmark spec**, the output is the following in html:

```html
<p><a href="foo):">link</a></p>
```

* this means that the link should have been `foo)`, where the escape character `\` should not have been added to the link; rather, it should have been cause to include the `)` as part of the link since it follows a backslash. 

* I think that the problem with the **lab 9 class implementation** is here:

```java
while (openParenCount > 0 && closeParen < markdown.length()) {
            if (markdown.charAt(closeParen) == '(') {
                openParenCount++;
            } else if (markdown.charAt(closeParen) == ')') {
                openParenCount--;
            }
            closeParen++;
        }
```

* the code assumes that the number of open and close parentheses are equal, which is consistent with the commonmark spec, **except** in the case where the parentheses is used as an escape character. If the program accounted for parentheses being used as part of the link text by the use of the backslash escape character, then it would work. 


## Second test file: `[link](<foo(and(bar)>)`

* I created another file in the respective directories for my repository and the class one on `ieng6`: 

```md
[link](<foo(and(bar)>)
```

* the output was the same for both my program and the class one (an empty list): 

```
[cs15lwi22aaw@ieng6-201]:lab5:105$ java MarkdownParse test-lab5-2.txt
[]
```

```
[cs15lwi22aaw@ieng6-201]:lab5mi:129$ java MarkdownParse3 test-lab5-2.txt
[]
```

* neither implementation is correct because the **commonmark spec** provides the following output in html:

```html
<p><a href="foo(and(bar)">link</a></p>
```

* which is a link which content enclosed in **`<...>`**. 
	
* the error in the class file is in the following method again (as this is another issue with unbalanced parentheses)

```java
static int findCloseParen(String markdown, int openParen) {
        int closeParen = openParen + 1;
        int openParenCount = 1;
        while (openParenCount > 0 && closeParen < markdown.length()) {
            if (markdown.charAt(closeParen) == '(') {
                openParenCount++;
            } else if (markdown.charAt(closeParen) == ')') {
                openParenCount--;
            }
            closeParen++;
        }
        if(openParenCount == 0) {
          return closeParen - 1;
        }
        else {
          return -1;
        }

    }
```

* Again, the class file does not account for the two exceptions in the **commonmark spec** for unbalanced parentheses, the second being when the parentheses are enclosed in the form `<...>`. 

* This causes the method above to return `-1` since it counts an extra open parentheses, and this ends up causing the program to return an empty ArrayList since the call to `finfCloseParen()` yielded `-1`. 

* to fix this error, the program should check for when a link has content enclosed within **`<...>`**. 
 










