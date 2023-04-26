**Browser --> Js Engine --> Call Stack**

**Web APIs**
    
    Set Timeout
    DOM APIs
    fetch()
    Local Storage
    Console
    Location
    
**Call Stack**

    It is a mechanism for tracking the execution of function calls
    Whenever a function is called, a new frame is added at the top of the call stack.
    It determines the order in which functions are executed.
    
**Callback Queue**

    It is a data structure that stores functions to be executed after the current code block has finished executing.
    These functions are executed at a later time, in response oto some event or conditions.
    
    setTimeout(function() {  //callback function
        console.log("Callback function called after 2 seconds");
    }, 2000);
    
**Event Loop**

    It is a mechanism that handles asynchronous code execution.
    It continuously checks the call stack and the callback queue to ensure that the code runs smoothly and does not block the main thread.
    
    
**Microtask Queue**

    When a JavaScript engine executes code, it first executes the current task. Once the current task is finished, it checks if there are any microtasks in the microtask queue. If there are, it executes them one by one until the queue is empty. Then, it moves on to the next task.
    It stores callback functions coming from promises and mutation observers
    
    console.log("Hello");
    
    setTimeout(function () {
       console.log("Callback queue's Callback function"); 
    }, 5000);
    
    fetch("https://api/fetch.com)
    .then(function () {
        console.log("Microtask queue's callback function");
    })
    
    ...........other code............
    
    First it will print "Hello"
    then it will execute other code present at the bottom.
    
    Once we got the api response, callback function associated with it, get store in microtask queue
    
    Once the set timeout timer expires, callback function associated with it, get store in callback queue
    
    Microtask queue has highest priority than Callback queue.
    
    Once the all functions present in Microtask queue gets executed, then callback queue functions will be executed.
    
    If Microtask queue is continuously getting filled with callback functions and if we are not getting chance to execute callback queue functions, then the starvation problem may arise.
    
**Mutation Observers**
    Mutation Observers is an API provided by modern browsers to monitor changes to the DOM (Document Object Model) tree in JavaScript.
    
    
    const fun1 = async () {
        const response = await axios(config);
        
        console.log("completed");
        console.log(response);
    }