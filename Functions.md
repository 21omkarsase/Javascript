**Function Statement / Declaration**

    Define a function using function keyword followed by function name, a list of parenthesis and a block of code in curly braces.
    
    function add(a, b) {
        return a + b;
    }


**Function Expressions**

    Define a function as a value of a variable. 
    
    const add = function(a, b) {
        return a + b;
    }
    
    
**function declaration                   vs               function expression**
-------------------------------------------------------------------------------------------

  They are hoisted                        |               They are not hoisted
  

**Anonymous Functions**

    An anonymous function in a function without a name.
    
    const add = function(a, b) {
        return a + b;
    }
    
    add(4, 5);
    
    
**Named Function Expressions**

    A named function expression is a function expression that has a name.
    
    we can use that function inside the body of that function.
    
    const mathOp = function add(a, b){
        console.log(add(3, 5));
        
        return a + b;
    }
    
    
**First Class Citizens/Functions**

    Functions are like first class citizens in js, which means that they are treated like any other value, such as number, string or object.
    
    Functions can be : 
        1. Assigned to variable or object property.
        2. Passed as argument to other function.
        3. Returned as values from functions.
        
        const createAdder = function(num1) {
            return function(num2) {
                return num1 + num2;
            };
        };

        const add5 = createAdder(5);

        console.log(add5(3)); 
    

**Arrow Functions**
    
    Shorthand syntax sor defining a function.
    
    const add = (a, b) =>{
        return a + b;
    }
    
    const add = (a, b) => a + b;
    

**Parameters**

    "Parameters" are the variables that are defined in the function declaration or expression. 
    They represent the values that the function expects to receive when it is called. 
    
    function addNumbers(num1, num2) {
        return num1 + num2;
    }
    

**Arguments**

    "Arguments" are the actual values that are passed to the function when it is called. 
    They are the values that are assigned to the function parameters. Here's an example:
    
    const sum = addNumbers(3, 5);
    

**Higher Order Functions**

    Function which takes another function as an input or returns a function is a higher order function.
    
    const square = (radius) => {
        return radius * radius;
    }
    
    const Area = (radius, square) => {
        return Math.PI * square(radius);
    }
    
    Area(3);