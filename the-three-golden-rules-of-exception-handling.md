# 

# The Three Golden Rules of Exception Handling

In this chapter we will learn that there are only **three **basic ** **or golden** rules** we should follow to do effective Java exception handling. The basis for chapter this was written down by Chris Adamson in December 2003 at [Java Today](http://today.java.net/pub/a/today/2003/12/04/exceptions.html). In short these three rules are:

1. **Be Specific**
2. **Throw Early**
3. **Catch Late**

In the next paragraphs we will discuss what that means in detail and how it is done.

## Be Specific

> Who the heck is **General Failure** and why he is **reading** my **hard drive**?

How often did we read a message like _An error has occurred_ and wished that there were more details what went wrong? Exactly!

The worst we can do is a

```java
throw new MyException("An error has occurred!");
```

or similar. We should at least include what went wrong and with what kind of entity. So a lot better would be

```java
throw new MyException("An error has occurred while reading customer record no " + customerNo);
```

Always provide contextual details so that a technical support can comprehend the situation of the exception. Of cause, chaining of exceptions always a good idea:

```java
throw new MyException("An error has occurred while reading customer record no " + customerNo, causingException);
```

The **silver bullet** or best -in-class solution would be to use **error codes **\(only once!\) as we might experienced them in enterprise software such as OracleDB \(ORA-Codes\). There are pattern to use Java enumerations \(enum classes\) to model such codes with I18N \(ResourceBundles\) and use the IDE usage search to find immediately the place where the exception was created.

## Throw Early

> **Never** put off till **tomorrow** what you can do **today**.

If an error situation occurs then we should signal it with an exception immediately and not later on. Here is an example how we should not do it:

```java
private static boolean configurationFileExists(final File  configuration) {
    return configuration !== null ? configuration.exists() : false;
}

public void readConfiguration() throws MyException {
    File configurationFile = new File("myconfiguration.ini");
    if (!configurationFileExists(configurationFile) {
        // throw late
        throw new MyException("Missing configuration: " + configurationFile.getAbsolutePath());
    }
}
```

We would better do it like this:

```java
private static void checkConfigurationFileExists(final File  configuration) throws MyException {
    if (configuration == null || !configuration.exists()) {
        // throw early
        throw new MyException("Missing configuration: " + configurationFile.getAbsolutePath());
    }
    //...
}

public void readConfiguration() throws MyException {
    File configurationFile = new File("myconfiguration.ini");
    checkConfigurationFileExists(configurationFile); // processing will end here if file is missing
    //...
}
```

Why is it better? Because the Exception stack trace is closer to the condition it causes which helps to comprehend the error in run time.

## Catch Late

> Scream if it hurts!

In Java there are only to real options how we can deal with exceptions:

1. **Catch** 'em \(all like Pokémons\) or
2. Use **throws** to not deal with them

A lot of developers think we have to do the first and handle the Exception. In many cases this is plain wrong. Very often it is very useful if we define a central place to deal with all exceptions. An Example is not so trivial like the both topics above. Let us say we have a [servlet class](https://en.wikipedia.org/wiki/Java_servlet) and implemented the [front controller pattern](https://en.wikipedia.org/wiki/Front_controller) the the central place to manage Exceptions is one of the do-methods in the servlet class the this would be the central place to deal with all kind of exceptions which are user input errors.

What we can observe very often is catching the exception and maybe log it. Or re-throw. Or both. This can be considered an anti-pattern and we will discuss this later.



