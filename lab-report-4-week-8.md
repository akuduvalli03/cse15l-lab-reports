# Lab Report Week 8: Debuggers

## Snippet 1: Backticks

* the code should produce the following list:

```java
["google.com","google.com", "ucsd.edu"]
```

* test in `MarkdownParseTest.java`:

```java
@Test
    public void testLabFile1() throws IOException {
        Path fileName = Path.of("testfiles/labtest1.md");
        String contents = Files.readString(fileName);
        assertEquals(List.of("google.com","google.com", "ucsd.edu"), MarkdownParse3.getLinks(contents));
    }
```

* My group's implementation's output:

```
There was 1 failure:
1) testLabFile1(MarkdownParseTest)
java.lang.AssertionError: expected:<[google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com, ucsd.edu]>
	at org.junit.Assert.fail(Assert.java:89)
	at org.junit.Assert.failNotEquals(Assert.java:835)
	at org.junit.Assert.assertEquals(Assert.java:120)
	at org.junit.Assert.assertEquals(Assert.java:146)
	at MarkdownParseTest.testLabFile1(MarkdownParseTest.java:20)
```


* The other group's implementation's output:

```
There was 1 failure:
1) testLabFile1(MarkdownParseTest)
java.lang.AssertionError: expected:<[google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com]>
	at org.junit.Assert.fail(Assert.java:89)
	at org.junit.Assert.failNotEquals(Assert.java:835)
	at org.junit.Assert.assertEquals(Assert.java:120)
	at org.junit.Assert.assertEquals(Assert.java:146)
	at MarkdownParseTest.testLabFile1(MarkdownParseTest.java:20)
```

* I think that for code snippets the `getLinks()` method could check for backticks separately so that the links can still be read properly without having an error. There could be a precedence for deciding what should be considered a link/link label/code block. Based out the output on commonmark, I think that when the text is inside the parentheses that correspond to a link, that it does not look at the backticks being a part of a code block. But when it is in the brackets that are for the link label, then the code block takes precedence such that it the link label could be in the code block style. 

## Snippet 2: Backticks

* the code should produce the following list:

```java
["google.com","google.com", "ucsd.edu"]
```

* test in `MarkdownParseTest.java`:

```java
@Test
    public void testLabFile1() throws IOException {
        Path fileName = Path.of("testfiles/labtest1.md");
        String contents = Files.readString(fileName);
        assertEquals(List.of("google.com","google.com", "ucsd.edu"), MarkdownParse3.getLinks(contents));
    }
```

* My group's implementation's output:

```
There was 1 failure:
1) testLabFile1(MarkdownParseTest)
java.lang.AssertionError: expected:<[google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com, ucsd.edu]>
	at org.junit.Assert.fail(Assert.java:89)
	at org.junit.Assert.failNotEquals(Assert.java:835)
	at org.junit.Assert.assertEquals(Assert.java:120)
	at org.junit.Assert.assertEquals(Assert.java:146)
	at MarkdownParseTest.testLabFile1(MarkdownParseTest.java:20)
```


* The other group's implementation's output:

```
There was 1 failure:
1) testLabFile1(MarkdownParseTest)
java.lang.AssertionError: expected:<[google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com]>
	at org.junit.Assert.fail(Assert.java:89)
	at org.junit.Assert.failNotEquals(Assert.java:835)
	at org.junit.Assert.assertEquals(Assert.java:120)
	at org.junit.Assert.assertEquals(Assert.java:146)
	at MarkdownParseTest.testLabFile1(MarkdownParseTest.java:20)
```

* I think that for code snippets the `getLinks()` method could check for backticks separately so that the links can still be read properly without having an error. There could be a precedence for deciding what should be considered a link/link label/code block. Based out the output on commonmark, I think that when the text is inside the parentheses that correspond to a link, that it does not look at the backticks being a part of a code block. But when it is in the brackets that are for the link label, then the code block takes precedence such that it the link label could be in the code block style. 



