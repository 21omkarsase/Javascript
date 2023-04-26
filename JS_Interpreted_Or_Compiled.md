**Interpreting**
    
    Interpreting involves reading and executing the source code line-by-line, without transforming the entire program into machine code ahead of time. 
    An interpreter reads the source code, translates each line into machine code, and immediately executes it. 
    
**Compiling**
    
    Compiling involves transforming the entire program into machine code ahead of time, before executing the program. 
    A compiler takes the entire source code, analyzes it, and generates an executable binary file, which can be directly executed by the computer's processor.

**JS is a interpreted or compiled language?**

    Js is often considered as interpreted language, but this is not entirely accurate.
    
    Js uses Just-In-Time compilation technique to execute the code.
    code is initially interpreted, but as the program executes, frequently used sections of code are identified and compiled into machine code for faster execution. 
    The compiled machine code is then cached for later use, so that subsequent executions of the same code can be executed without the need for further compilation.
    
**Working Of JS Engine**

    Lexical analysis/tokenization:
    The engine takes in the source code and breaks it down into individual tokens such as keywords, operators, literals, etc. through a process called lexical analysis or tokenization.

    Parsing:
    The tokens are then parsed into an abstract syntax tree (AST), which represents the structure of the code. During parsing, the engine analyzes the structure of the code and builds an AST, which provides a more abstract representation of the code than the tokens.

    Compilation:
    The AST is then compiled into machine code, which can be executed by the computer's processor. This process typically involves optimizing the code for performance, such as by eliminating unnecessary operations and inlining functions. During compilation, the engine converts the AST into executable machine code.

    Interpretation:
    The compiled code is executed line by line by the engine's interpreter, which executes the code and produces the expected results. During interpretation, the engine performs various tasks such as resolving variable and function references, executing loops and conditionals, and handling exceptions.

    Garbage collection:
    The engine also manages memory allocation and deallocation, such as by performing garbage collection to reclaim memory occupied by objects that are no longer needed by the program. During this phase, the engine identifies objects that are no longer needed and frees up the memory they were occupying.