**Block Scope**

    Block is declared with help of curly braces -> {}
    To execute or group multiple statements we use block
    e.g At time of loops, functions, and if-else statements
       
{
    var a = 10;
    let b = 20;
    const c = 30;
}

    b, c won't be stored inside global scope (because of let and const declaration).
    Instead of global scope, they will be stored inside block scope.
    a will be stored inside global scope (because of var declaration)
    
    if we try to access a outside block scope there won't be any problem
    but for b and c ->  ReferenceError: a || b is not defined
    
**Shadwoing**

    var a = 100;                        |
    let b = 200;                        |              Will be stored inside scope named "Script"
    {                                   |
        var a = 10;                     |
        let b = 20;                     |               Will be stored inside scope named "Block"
        const c = 30;                   |
        console.log(a);                 |               10
        console.log(b);                 |               20
        console.log(c);                 |               30
    }                                   |
    try {                               |
        console.log(a);                 |               10
    } catch (error) {                   |
        console.log(undefined);         |
    }                                   |
    try {                               |
        console.log(b);                 |               200
    } catch (error) {                   |
        console.log(undefined);         |
    }                                   |
    try {                               |
        console.log(c);                 |
    } catch (error) {                   |
        console.log(undefined);         |               undefined
    }                                   |
    
    In above code
        after declaration of a (inside block scope)
        a will refer to same memory location inside global scope -> 10
        
        a shadows it's previous value (because of var declaration and global scope)
        
        In case of b it won't able to shadow it's previous value as b is declared using let and variables declared using let are always block scoped.
    
    We can't shadow let variable present outside block scope with var variable present inside block scope
        let a = 10;
        {
            var a = 20;
        }
    but we can do vice-versa
        var a = 10;
        {
            let a = 20;
        }
    
    and we can always shadow let with let or const with const