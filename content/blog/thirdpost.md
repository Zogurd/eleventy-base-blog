---
title: Intro To JavaScript - Functions and Control Flow
description: This post is an introduction to JavaScript and the used of functions with statements.
date: 2023-11-19
tags:
---
<div class="container">
	<h4 class="d-flex justify-content-center">Task 1 - Percentage Calculator</h4>
	<p class="h6 d-flex justify-content-center">Create a function that is able to return a specific percentage of any number (For example you want to know what 30% of 135 is).</p>
	<ol class="d-grid justify-content-center">
		<li>Create a function named percentageCalculator</li>
		<li>Add 2 arguments for “number” and “percentage”</li>
		<li>Do the maths required to work out a percentage with the arguments</li>
		<li>Return the result of the maths</li>
		<li>Console.log the returned value</li>
	</ol>
	<br>
	<p class="h6 d-flex justify-content-center">(Below is my solution to task 1. I also used boostrap to style the whole HTML document.)</p>
</div>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Percentage Calculator</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
</head>
<body class="bg-dark text-light">
    <!-- Name for Programe -->
    <h1 class="container d-flex justify-content-center align-items-center text-info my-5">Percentage Calculator:</h1>
    <br>
    <!-- The Function displays output here once called -->
    <p class="d-flex justify-content-center align-items-center h4" id="myOutput">0</p>
    <br>
    <div class="container d-flex justify-content-center mt-5">
        <!-- User input field for a number to get a percentage from -->
        <div class="px-5">
            <label class="mb-2" for="numberToUse">Number:</label>
            <input class="w-100" type="text" id="numToUse" placeholder="Enter amount...">
        </div>
        <!-- User input field for percentage -->
        <div class="px-5">
            <label class="mb-2" for="percentAmmount">Percentage:</label>
            <input class="w-100" type="text" id="percentAmmount" placeholder="Enter percent...">
        </div>
    </div>
    <br>
    <!-- Button to call the function -->
    <div class="d-grid gap-2 col-4 mx-auto">
        <button class="btn btn-info" id="calcBtn" type="button">Calculate</button>
    </div>
    <script src="./percentCalc.js"></script>
</body>
</html>
```

<br>

```js
document.getElementById("calcBtn").onclick = function percentageCalc(numToUse, percentAmmount) {

// Declaring variables for later use
    let total;

// getting the values from the user that is put in the input field
    numToUse = Number(document.getElementById("numToUse").value);

// getting the values from the user that is put in the input field
    percentAmmount = Number(document.getElementById("percentAmmount").value);

// I used an if statement to calculate and display an output to the DOM weather the user enters values or not
    if (numToUse > 0 && percentAmmount >= 0) {
        total = (numToUse * percentAmmount) / 100;
        total = Number(total);
        document.getElementById("myOutput").innerHTML = `${percentAmmount}% of ${numToUse} is, ${total}`;
    } 
    else {
        document.getElementById("myOutput").innerHTML = "Enter a number and percent to calculate...";
    }
    console.log(total);
```
<br>
<div>
	<h4 class="d-flex justify-content-center">Task 2 - Switch Statement</h4>
	<p class="h6 d-flex justify-content-center">Customers can order 3 different types of drink and also select 3 sizes. Cola, Lemonade and  Orangeade as well as Small, Medium and Large.<br>The button they press have the values “cola”,”lemon”,”orange”
	</p>
	<p class="h6 d-flex justify-content-center">Create a function that will output the message “You have ordered a {size} of {softDrinkLabel}”:</p>
	<ol class="d-grid justify-content-center">
		<li>Create a function named drinkOrder</li>
		<li>Add 2 arguments for “size” and “drink”</li>
		<li>Use a switch statement to determine where the functional code needs to be written</li>
		<li>Create a message in each case statement to be returned.</li>
		<li>Console.log the returned message</li>
	</ol>
	<br>
	<p class="h6 d-flex justify-content-center">(Below is my solution to task 2. I also used boostrap to style the whole HTML document.)</p>
</div>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Drink Order</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
</head>
<body class="bg-dark text-light">
    <!-- Name for Programe -->
    <h1 class="container d-flex justify-content-center align-items-center text-info mt-3">Drinks Menu:</h1>
    <br>
    <!-- User input fields for drink type -->
    <div class="d-grid justify-content-center w-100">
        <div>
            <h5 class="d-flex justify-content-center text-secondary text-decoration-underline">Flavour's</h5>
            <label>
                <input type="radio" name="drink" value="lemon"> Lemonade
            </label>
            <br>
            <label>
                <input type="radio" name="drink" value="orange"> Orangeade
            </label>
            <br>
            <label>
                <input type="radio" name="drink" value="cola"> Cola
            </label>
            <div class="container border border-info my-3"></div>
    <!-- User input field for drink size -->
            <h5 class="d-flex justify-content-center text-secondary text-decoration-underline">Size's</h5>
            <label>
                <input type="radio" name="size" value="sm"> Small
            </label>
            <br>
            <label>
                <input type="radio" name="size" value="md"> Medium
            </label>
            <br>
            <label>
                <input type="radio" name="size" value="lg"> Large
            </label>
        </div>
    </div>
    <br>
    <!-- Button to call the function -->
    <div class="d-grid gap-2 col-4 mx-auto">
        <button class="btn btn-info" id="orderBtn" type="button">Order</button>
    </div>
    <br>
    <br>
    <!-- The Function displays output here once called -->
    <div class="container d-flex justify-content-center h6">
        <p id="myOutput">...</p>
    </div>
    <script src="./drinkOrder.js"></script>
</body>
</html>
```

<br>

```js
// Used a button to call the function that outputs to the DOM at the end
document.getElementById("orderBtn").onclick = 
    function drinkOrder(drink, size) {
        
        // getting the drink value thats been selected in the set of radio buttons for the switch statement
        drink = document.querySelector('input[name="drink"]:checked').value;

        // getting the size value thats been selected in the set of radio buttons for the switch statement
        size = document.querySelector('input[name="size"]:checked').value;
        
        // empty variable used to assign the string related to the selected radio
        let drinkLabel;

        // empty variable used to assign the string related to the selected radio
        let sizeLabel;

        // Switch for the dink slected
        switch (drink) {

            case "lemon":
                drinkLabel = 'Lemonade';
                break;

            case "orange":
                drinkLabel = 'Orangeade';
                break;

            case "cola":
                drinkLabel = 'Cola';
                break;

            default:
                drinkLabel = drink;
                break;
        }
        
        // Switch for the size selected
        switch (size) {

            case "sm":
                sizeLabel = 'small';
                break;

            case "md":
                sizeLabel = 'medium';
                break;

            case "lg":
                sizeLabel = 'large';
                break;

            default:
                sizeLabel = size;
                break;

        }
        
        // Prints to the DOM
        document.getElementById("myOutput").innerHTML = 
            `You have ordered a ${sizeLabel} ${drinkLabel}.`;

        console.log(`You have ordered a ${sizeLabel} ${drinkLabel}.`);
    }



/*
This can also be done in 4 lines as shown below:

document.getElementById("orderBtn").onclick = function drinkOrder(drink, size) {
    drink = document.querySelector('input[name="drink"]:checked').value;
    size = document.querySelector('input[name="size"]:checked').value;
    document.getElementById("myOutput").innerHTML = `You have ordered a ${size} ${drink}.`;
}
*/
```
<br>
<div>
	<h4 class="d-flex justify-content-center">Task 3 - Calculator</h4>
	<p class="h6 d-flex justify-content-center">We need to create a function capable of using the addition, subtraction, multiply, divider or modulus operator on 2 numbers provided.</p>
	<ol class="d-grid justify-content-center">
		<li>Create a function named calculator</li>
		<li>Add 3 arguments for “number1”, “number2” and “operator”</li>
		<li>Use a switch statement to determine which operator to use</li>
		<li>Add the math code for each operator in the case statement to return the value</li>
		<li>Console.log a message “{number1} {operator} {number2} = {value}”</li>
	</ol>
	<br>
	<p class="h6 d-flex justify-content-center">(Below is my solution to task 3. I also used boostrap to style the whole HTML document.)</p>
</div>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator(With JS switch)</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
</head>
<body class="bg-dark text-light">
    <div class="container">
        <h1 class="d-flex justify-content-center mt-3 pt-3"><span class="text-info">My</span>Calculator</h1>
        <h5 class="d-flex justify-content-center">(With JS switch)</h5>
        <p class="d-flex justify-content-center text-info mt-4">Operators are:</p>
        <ul class="d-grid justify-content-center">
            <li>divide = /</li>
            <li>multiply = *</li>
            <li>addition = +</li>
            <li>subtract = -</li>
        </ul>
        <div class="container d-grid justify-content-center mt-5">
            <label>Number: <input type="text" id="num1" placeholder="Enter a number"></label>
            <br>
            <label>operator: <input type="text" id="op" placeholder="Only use: /, *, -, +"></label>
            <br>
            <label>Number: <input type="text" id="num2" placeholder="Enter a number"></label>
        </div>
        <br>
        <div class="d-flex justify-content-center mt-3 px-5">
            <button class="btn btn-info w-50" onclick="calculator()">Click here to do the Math</button>
        </div>
        <br>
        <div class="d-flex justify-content-center mt-3 px-5">
            <p class="h3" id="myOutput">. . .</p>
        </div>
    </div>
    <script src="./calcWithSwitch.js"></script>
</body>
</html>
```

<br>

```js
function calculator(a, operator, b) {

    a = document.getElementById("num1").value;
    operator = document.getElementById("op").value;
    b = document.getElementById("num2").value;

    let out;

    switch (operator) {

        case '-':
            operator = "minus";
            out = a - b;
            break;

        case '*':
            operator = "multiplied by";
            out = a * b;
            break;

        case '/':
            operator = "divided by";
            out = a / b;
            break;

        case '+':
            operator = "plus";
            out = a + b;
            break;
        }
    
        document.getElementById("myOutput").innerHTML = `The total of ${a} ${operator} ${b} = ${out}`;
        console.log(`The total of ${a} ${operator} ${b} = ${out}`);
};
```