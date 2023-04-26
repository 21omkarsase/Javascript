**Hoisting**
 
    It is a behavior in which variable and function declarations are moved to the top of their respective scopes during the compilation phase of the code execution.
    This means that even if a variable or function is declared and initialized later in the code, it can still be used before its declaration.
    

**How it works**

    getName();
    console.log(x);
    
    function getName(){
        console.log("Omkar Sase");
    }
    
    var x = 10;
    
    In the first phase of allocation of memory.
    Each variable and function will be stored inside memory component of execution context.
    
    So, at time of execution if we are calling getName() or logging value of x even before their declaration, it will not throw an error.
    
    Instead it will log "undefined" for x and whole function code for getName().
    
    
    In case of an arrow function ->
    var getName = () => {
        console.log("Omkar Sase")
    }
    
    It will be treated as variable and instead of storing whole function code "undefined" will be stored in memory component.
    
    We will get an error like : TypeError: getName is not a function
    