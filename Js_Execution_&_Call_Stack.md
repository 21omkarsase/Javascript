Simple JS program
    
    var n = 2;
    function square (num) {
        var ans = num * num;
        return ans;
    }
    var square2 = square(n);
    var square4 = square(4);
    
Execution Context
    
    Memory                           |   Code
    ---------------------------------|-----------------------------------------------
    n : undefined                    | code is executed line by line
    square : {whole function code}   | 
    square2 : undefined              | a new execution context would be created for
    square4 : undefined              | every function inside the code component
    
    First time memory allocated to all the variables and functions.
    In second phase code will be executed line by line.
        Undefined values will be replaced with calculated / real values.
        Function code will be executed line by line by creating new execution context.
        This local execution context will be deleted after the completion of the function
    After all the code get executed, global execution context will be deleted
    
Call Stack
    
    |                       |
    |                       |
    |                       |
    |                       |
    |  square4 call         |
    |  square2 call         |
    |  global execution call|
    __________________________