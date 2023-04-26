**Closures**

    Closure is a function that has access to variables it it's outer lexical environment, even after that outer function has returned the inner(closure) function.
    
    
    function a() {
        let x = 10;
        function b() {
            let x = 100;
            function c() {
                console.log(x);
            }
            return c;
        }
        const y = b();
        return y;
    }

    let z = a();

    z();
    
    Here z is a closure function, that has access to value of x which is present inside it's parents lexical environment.
    
    Uses of closures : 
        Module Design Pattern
        Currying
        Functions like once
        Memoize
        Maintaining state in async world
        SetTimeouts
        Iterators
        Data Hiding & Encapsulation 

**Closures With SetTimeout**

    setTimeout remembers it's lexical environment. Therefore while using var it points to the same memory location and at time of let it creates new copy of 'i' every time.
    
    const fun = () => {
        for (let / var i = 1; i <= 5; i++) {     
            setTimeout(() => {
                console.log(i);
            }, i * 1000);
        }
    }
    fun();
    
    If we use let over here we will get same value after each second (var : global scope)
    But, if we use let, it will log different value of variable i. (let : block scope). 
    To do this only using var : 
        const fun = () => {
        for (var i = 1; i <= 5; i++) {
                fun close (x) {
                    setTimeout(() => {
                        console.log(x);
                    }, x * 1000);
                }
                close(i);          // New copy of 'i' will be passed every time
            }
        }
        fun();
        
        Data Hiding & Encapsulation  :
            function counter() {
                var count = 0;
                return function incrementCount() {
                    count++;
                    console.log(count);
                }
            }
            
            counter()();
            
            We can't access count variable directly from outside the counter function.
            If we try logging 'count' from outside we will get ReferenceError.
            
            counter()(); This line will create new copy of counter function, and count will again start from 0.
            
            var counter1 = counter();
            
            counter1();
            counter1();
                This will not create new copy of counter function. Instead it will remember value of count from it's lexical environment and count will increased by 1. 

**Closure with constructor functions**
        
    function Counter() {
        var count = 0;
        
        this.incrementCount = function() {
            count++;
            console.log(count);
        }
        
        this.decrementCount = function() {
            count--;
            console.log(count);
        }
    }
    
    var counter1 = new Counter();
    
    counter1.incrementCount();
    counter1.incrementCount();
    counter1.decrementCount();
    
    This will work same. 
    This is a much clean and scalable way.
    
**Disadvantages Of Closures**
    
    Over consumption of memory.
    If not handled properly, they can lead to memory leak.
    Variables present inside lexical environment are not garbage collected once the program ended. As in future we may execute those closure functions again.
    
**Garbage Collection In Js**

    In Javascript engines garbage collector takes out unused variables and frees up memory whenever they are no longer needed.
    
    But in case of closures it can't takes those variables out of memory, as they are present inside lexical scope of closure function, which may needed in future when we execute closure function.
    
    function fun1() {
        var x = 10, y = 20;
        return function logX() {
            console.log(x);
        }
    }
    
    var inFun = fun1();
    
    We can execute 'inFun' in future, therefore variable 'x' will not be collected by garbage collector.
    
    **Smart Garbage Collection**
        JS engines like chrome takes out other unused variables from lexical environment of closure function which are not needed in future(Like variable 'y' in above code)
            
