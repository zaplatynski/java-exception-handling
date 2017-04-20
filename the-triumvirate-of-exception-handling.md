# The Triumvirate Of Exception Handling

In this chapter will leran that there are three base categories in Java which can be used to signal abnormal program behavior:

1. **Errors**
2. **Checked Exceptions**
3. **Unchecked Exceptions**

In the next paragraphs we will discuss how they are represented and how they are used in Java programs.

## How The Three Categories Map To Java Classes

Let us have a look to this table to see how the mapping is taking place:

| _**Category**_ | _**Java Class**_ |
| :--- | :--- |
| **Errors** | java.lang.**Error** |
| **Checked Exception** | java.lang.**Exception** |
| **Unchecked Exception** | java.lang.**RuntimeException** |

In UML representation we get this class diagram which shows a certain structure:

![](/assets/UMLexceptions.png)

While **Error** and **Exception** are direct descendants from **Throwable**, **RuntimeException** is a child of Exception as the name already reveals. How should be this relevant for us? With this three base types there comes a specific philosophy which we want to discuss in detail in the next paragraphs.

## Errors

## Checked Exceptions

## Unchecked Exceptions



