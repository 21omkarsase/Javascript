**Global Space**
    Any thing which is not inside the function code is considered to be part of global space
    e.g
        var x = 10;                  Global Space
        function getName(){          Global Space
            var x = 100;             Local Space
        }
    
**this** keyword
    Globally it refers to window object.
    this === window => true
    
    var x = 10;  Inside global space
    
    console.log(window.x);
    console.log(this.x);
    