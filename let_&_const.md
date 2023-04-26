**let & const declarations are also hoisted in js**
temporal dead-zone for the time being

    variables or functions declared using let || const can't be accessed before the value get's assigned to them
    
    these variables are functions are kept inside the temporal dead-zone which don't falls under global space
    
    console.log(a);
    
    let a = 10;
    
    we will get ReferenceError : can't access a before it's initialization 
    we can only access it after value 10 gets assigned to a
    
    but it would be wrong to say that these variables are not hoisted.
    
    these will also be declared as undefined, but not inside global space. That's why we get an reference error. 
    
    let a = 10;
    var b = 20;
    
we won't able to access a with "window" object or with "this" keyword.
  
    window.a || this.a => undefined
    window.b || this.b => 20
    
    
In case of let & const we can't declare variables or functions with same name like var
    
    var x = 10;   var x = 20   -> possible
    let x = 10;   let x = 20   -> not possible   (SyntaxError)
    
**Put your all declaration at top of code to avoid temporal dead-zone**