---
title: Loops, Arrays & Objects Part 2
description: This post is about JavaScript loops, arrays and objects.
date: 2023-12-07
tags:
---
```js
                                                /* LOOPS, ARRAY & OBJECTS (week 2) */

// TASK 1  - Shopping Cart
let shoppingCart = [
    { name: "loaf of bread", type: "food", quantity: 1, price: 0.85 },
    { name: "multipack beans", type: "food", quantity: 1, price: 1 },
    { name: "mushrooms", type: "food", quantity: 10, price: 0.1 },
    { name: "can of beer", type: "alcohol", quantity: 4, price: 1.1 },
    { name: "prosecco", type: "alcohol", quantity: 1, price: 8.99 },
    { name: "steak", type: "food", quantity: 2, price: 3.99 },
    { name: "blue cheese", type: "food", quantity: 1, price: 2.99 },
    { name: "candles", type: "home", quantity: 3, price: 1.99 },
    { name: "cheesecake", type: "food", quantity: 1, price: 4.99 },
    { name: "onions", type: "food", quantity: 3, price: 0.4 }
];

/*
Part 1
    - Create a function that takes 1 argument (the array)
    - Create a variable inside the function called “totalPrice”
    - Loop through each item in the array and add the value of the item to the total price, remember to account for the quantity.
    - Return the totalPrice Variable
    - Console.log the returned value
*/
function firstCartTotal(cart) {
    let totalPrice = 0;
    for (const item of cart) {
        let itemTotal = item.price * item.quantity;
        totalPrice += itemTotal;
    }
    return totalPrice.toFixed(2);
};
console.log(`The total of the cart for part 1 is £${firstCartTotal(shoppingCart)}`);

/*
Part 2
    - Create a function that takes 1 argument (the array)
    - Create a variable inside the function called “totalPrice”
    - Loop through each item in the array and add the value of the item to the total price, remember to account for the quantity. 
    - If the item has a type of “food” the total price is 20% less
    - Return the totalPrice Variable
*/
function secondCardTotal(cart) {
    let totalPrice = 0;
    for (const item of cart) {
        let itemTotal = item.price * item.quantity;
        if (item.type === "food") {
            const discount = (itemTotal * 20) / 100;
            itemTotal -= discount;
        }
        totalPrice += itemTotal;
    }
    return totalPrice.toFixed(2);
}
console.log(`The total of the cart for part 2 is £${secondCardTotal(shoppingCart)}`)

/*
Part 3
    - Add 2 extra arguments to the function for “discountAmount” and “type”
    - Replace the logic that takes off 20% for object.type == “food” for object.type == type and allow the 20% to be the {discountAmount}%
    - Create logic so that if type == “any” all products have a discount applied
*/
function thirdCartTotal(cart, discountAmount, type) {
    let totalPrice = 0;
    for (const item of cart) {
        let itemTotal = item.price * item.quantity;
        if (type === item.type || type === "any") {
            const discount = (itemTotal * discountAmount) / 100;
            itemTotal -= discount;
        };
        totalPrice += itemTotal;
    }
    return totalPrice.toFixed(2);
};
console.log(`The total of the cart for part 3 is £${thirdCartTotal(shoppingCart, 20, 'any')}`);

/*
Part 4
We are going to be using an array of objects provided as a simple shopping cart example.
We need to be able to work out which items cost between 2 price points. So for example, we need the cart to be returned by which products cost more than £2 but less than £5.
    - Create a function that has 3 arguments “cart”, “lowPrice” and “highPrice”
    - Create an empty array called arrItems at the start of the function.
    - Loop through each item of the array
    - If the price value is higher than or equal to the lowPrice and lower than or equal to the highPrice push to arrItems
*/
function forthCartTotal(cart, lowPrice, highPrice) {
    const items = [];
    for (const item of cart) {
        if (item.price >= lowPrice && item.price <= highPrice) {
            items.push(` ${item.name} - £${item.price}`);
        };
    }
    return items;
};
console.log(`The item(s) in the cart for part 4 between the selected price range's are: ${forthCartTotal(shoppingCart, 2, 6)}`);

/*
Part 5
    - Add an additional argument to the function “quantity” this is going to be a boolean
    - If quantity == true then account for the total price with the quantity included as being between lowPrice and highPrice
*/
function fifthCartTotal(cart,  lowPrice, highPrice, quantity) {
    const items = [];
    for (const item of cart) {
        if(quantity === true) {
            if (item.price * item.quantity >= lowPrice && item.price * item.quantity <= highPrice) {
                items.push(` (${item.quantity}) ${item.name} - £${item.price} each`);
            }  else if (item.price >= lowPrice && item.price <= highPrice){
                items.push(` ${item.name} - £${item.price} each`)
            };
        };
    }
    return items;
};
  
console.log(`The item(s) in the cart for part 5 between the selected price range's including quantities are: ${fifthCartTotal(shoppingCart, 4, 10, true)}`);


/*
                                                            Additional Tasks
                We are going to be creating a function that is able to take all of the values of an array and return the average.
*/

/*
Part 1
The function will be able to return the mode, median or mean of the numbers.
    - Create an array of random numbers
    - Create a function that takes 1 argument (the array) which can work out the mean of the numbers provided
    - Create a function which can work out the mode of the numbers provided
    - Create a function which can work out the median of the numbers provided
*/
const numArray = [5, 10, 12, 12, 8, 5, 5, 14, 9];

// Mean
function mean(myNums) {
    let total = 0;
    for (let i = 0; i < myNums.length; i ++) {
        total += myNums[i];
    }
    return total / myNums.length;
};
console.log("mean = " + mean(numArray));

// Median
function median(myNums) {
    let median = 0;
    let arrayLength = myNums.length;
    myNums.sort();
    if(arrayLength % 2 === 0){
        //To check if numArray has an even amount of numbers
        median = (myNums[arrayLength / 2 - 1] + myNums[arrayLength / 2]) / 2;
    } else {
        //To check if numArray has an odd amount of numbers
        median = myNums[(arrayLength - 1) / 2];
    }
    return median;
};
console.log(`median = ${median(numArray)}`);

// Mode
function mode(myNums) {
    const frequencyTable = {};
    myNums.forEach(elem => frequencyTable[elem] = frequencyTable[elem] + 1 || 1);
    let modes = [];
    let maxFrequency = 0;
    for (const key in frequencyTable) {
        if (frequencyTable[key] > maxFrequency) {
            modes = [Number(key)];
            maxFrequency = frequencyTable[key];
        } else if (frequencyTable[key] === maxFrequency) {
            modes.push(Number(key));
        }
    };
    if (modes.length === Object.keys(frequencyTable).length) modes = [];
    return modes;
}
console.log(`mode = ${mode(numArray)}`); 

/*
Part 2
    - Create a new function which takes 2 arguments (the array and a type variable).
    - Create a switch statement which has the cases ‘mode’, ‘median’ and ‘mean’
    - Copy and paste the functionality from your 3 previous functions into the case statement
    - Return the required number based on the arguments passed.
*/

function methodToUse(array, type) {
    switch(type) {
        case "mean":  
            console.log("mean = " + mean(array));
            break;
        case "median": 
            console.log(`median = ${median(array)}`);
            break;
        case "mode": 
            console.log(`mode = ${mode(array)}`); 
            break;
        default:
            console.log(`Please enter a valid array with a valid method type!`)
    }
};

methodToUse([46, 47, 87, 45, 45, 56, 58, 56], "median");
methodToUse(numArray, "mode");
```