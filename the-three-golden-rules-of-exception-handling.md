# 

# The Three Golden Rules of Exception Handling

In this chapter we will learn that there are only **three **basic ** **or golden** rules** we should follow to do effective Java exception handling. The basis for chapter this was written down by Chris Adamson in December 2003 at [Today Java](http://today.java.net/pub/a/today/2003/12/04/exceptions.html). In short these three rules are:

1. **Be Specific**
2. **Throw Early**
3. **Catch Late**

In the next paragraphs we will discuss what that means in detail and how it is done.

## Be Specific

> Who the heck is **General Failure** and why he is **reading** my **hard drive**?

How often did we read a message like _An error has occurred_ and wished that there were more details what went wrong? Exactly!

The worst we can do is a

```java
throw new Exception("An error has occurred!");
```

or similar. We should at least include what went wrong and with what kind of entity. So a lot better would be

```java
throw new Exception("An error has occurred while reading customer record no " + customerNo); 
```

## Throw Early

## Catch Late





