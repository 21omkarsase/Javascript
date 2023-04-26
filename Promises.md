**Promises**

    a Promise is an object representing the eventual completion or failure of an asynchronous operation, such as a network request, a file read/write operation, or a database query. 
    
    A Promise is essentially a placeholder for a value that is not yet available, but will be at some point in the future.
    
    Promises in JavaScript are commonly used to handle asynchronous operations and avoid callback hell, where multiple nested callbacks are required to handle a series of asynchronous operations. 
    
    const user = fetch("http://api.github.com/users/21omkarsase)
    
    fetch returns promise. We can handle it's response by .then and .catch methods.
    
    user.then((data) => {
        console.log(data);
    })
    
    In this way we are able to solve problem of "Inversion Of Control", which we were facing due to callbacks.
    
    Avoiding Callback Hell with promises
        
        const card = ["shoes", "pants", "kurta"]
        
        
        Using Callbacks
        createOrder(cart, (orderId) => {
            proceedToPayment(orderId, (paymentSlip) => {
                showOrderSummary(paymentSlip, (paymentInfo) => {
                    updateWalletBalance(paymentInfo);
                })
            })
        })
        
        Using Promises
        function createOrderPromise(cart) {
        return new Promise((resolve, reject) => {
            createOrder(cart, (orderId) => {
            if (orderId) {
                resolve(orderId);
            } else {
                reject('Error: Could not create order');
            }
            });
        });
        }

        function proceedToPaymentPromise(orderId) {
        return new Promise((resolve, reject) => {
            proceedToPayment(orderId, (paymentSlip) => {
            if (paymentSlip) {
                resolve(paymentSlip);
            } else {
                reject('Error: Could not proceed to payment');
            }
            });
        });
        }

        function showOrderSummaryPromise(paymentSlip) {
        return new Promise((resolve, reject) => {
            showOrderSummary(paymentSlip, (paymentInfo) => {
            if (paymentInfo) {
                resolve(paymentInfo);
            } else {
                reject('Error: Could not show order summary');
            }
            });
        });
        }

        function updateWalletBalancePromise(paymentInfo) {
        return new Promise((resolve, reject) => {
            try {
            updateWalletBalance(paymentInfo);
            resolve();
            } catch (error) {
            reject('Error: Could not update wallet balance');
            }
        });
        }
        
        createOrderPromise(cart)
        .then(orderId => proceedToPaymentPromise(orderId))
        .then(paymentSlip => showOrderSummaryPromise(paymentSlip))
        .then(paymentInfo => updateWalletBalancePromise(paymentInfo))
        .then(() => {
            console.log('Order processed successfully!');
        })
        .catch(error => console.error(error));
        
        Using Async Await
        async function processOrder(cart) {
            try {
                const orderId = await createOrderPromise(cart);
                const paymentSlip = await proceedToPaymentPromise(orderId);
                const paymentInfo = await showOrderSummaryPromise(paymentSlip);
                await updateWalletBalancePromise(paymentInfo);
                console.log('Order processed successfully!');
            } catch (error) {
                console.error(error);
            }
        }();
        
    "await" Keyword : 
        When you use the await keyword in front of a Promise, the code execution is paused at that point until the Promise resolves. Once the Promise resolves, the value it resolves with is returned and the code execution continues.
        
    "Promise Chaining" : 
        Promise chaining is a technique in JavaScript for handling a sequence of asynchronous operations that depend on the results of previous operations.
