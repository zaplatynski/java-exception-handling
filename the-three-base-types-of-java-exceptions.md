# The Three Base Types

We all know there are three base types in Java which can be used with the keywords **throws** or **throw**:

1. **Error**
2. **Exception**
3. **RuntimeException**

In UML representation we get this class diagram which shows a certain structure:

![](/assets/UMLexceptions.png)

While **Error** and **Exception** are direct descendants from **Throwable**, **RuntimeException** is a child of Exception as the name already reveals. How should be this relevant for us? With this three base types there comes a specific philosophy which we want to discuss in detail in the next paragraphs.



