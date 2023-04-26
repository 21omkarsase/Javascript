**code**
    
    var x = 1;
    
    function a(){
        var x = 10;
        b();
        function b(){
            var x = 100;
            console.log(x);
        }
    }
    
    a();
    
    1. function a() is present inside lexical environment of global space
    2. function b() is present inside lexical environment of function a's local space
    
    3.At time of : console.log(x)
        It will search for x inside function b
            It it don't get x inside b(), it will search for b inside it's parent lexical environment i.e function a()
                If it don't get x inside a() also, then it will search for  b inside it's parent lexical environment i.e. global space.
                    It it don't get x inside global space, then it will give an error : x is not defined.