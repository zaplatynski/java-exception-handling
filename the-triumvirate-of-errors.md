# The Triumvirate Of Errors

Three base categories in Java which can be used to signal abnormal program behavior:

1. **Errors**
2. **Checked Exceptions**
3. **Unchecked Exceptions**

_**TODO: make connection between cats and classes**_

In UML representation we get this class diagram which shows a certain structure:

![](/assets/UMLexceptions.png)

While **Error** and **Exception** are direct descendants from **Throwable**, **RuntimeException** is a child of Exception as the name already reveals. How should be this relevant for us? With this three base types there comes a specific philosophy which we want to discuss in detail in the next paragraphs.

