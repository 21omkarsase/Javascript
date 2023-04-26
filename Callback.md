**Callback Functions**

    A callback function is a function that is passed as an argument to another function and is executed inside the calling function. 
    Callback functions are commonly used in JavaScript for asynchronous programming.
    Where a function needs to wait for an external process  to complete before executing.
    
    const fun1 = (sum) => {
        console.log(sum);
    }

    const fun2 = (a, b, fun1) => {
        fun1(a + b);
    }

    fun2(5, 2, fun1);


**Callback functions with closures**
    function Counter() {
        var count = 1;
        
        this.increment = function () {
            count++;
            console.log(count);
        }
        
        this.decrement = function () {
            count--;
            console.log(count);
        }
    }
    
    const counter1 = new Counter();
    
    function logAndIncrement (callback) {
        console.log("Incrementing");
        callback.increment();
    }
    
    function logAndDecrement (callback) {
        console.log("Decrementing");
        callback.decrement();
    }
    
    logAndIncrement(counter1);
    logAndDecrement(counter1);
    
    
**Callback Functions With Event Listeners**

    const btn = document.querySelector("#btn");
    
    function addEventListeners () {
        let count = 1;
        btn.addEventListener("click", function () {
            console.log("btn clicked", ++count);
        });
    }
    
    addEventListeners();
    
    
    Remove the event listeners when not needed. As they are not garbage collected
    btn.removeEventListener("click", clickHandler);
    
    const btn = document.querySelector("#btn");

    function addEventListeners() {
        let count = 1;

        function clickHandler() {
            console.log("btn clicked", ++count);
        }

        btn.addEventListener("click", clickHandler);

        return function () {
            btn.removeEventListener("click", clickHandler)
        };
    }

    const removeListener = addEventListeners();

    removeListener();

    The count variable will no longer be in scope and can be garbage collected if there are no other references to it.