---
title: Programming Concepts
description: This post is about programming concepts completed via The Coders Guild.
date: 2023-11-04
tags: 
---
<div class="container">
    <h4 class="d-flex justify-content-center">1- Make a program to calculate a tip</h4>
    <ul class="d-grid justify-content-center">
        <li>Create variables for the pre-tip total and the tip percentage</li>
        <li>Calculate the new total</li>
        <li>Output a sentence to the page - something like: Your total bill, with tip, is £35.45</li>
    </ul>
    <h6 class="d-flex justify-content-center">BONUS POINTS:</h6>
    <ul class="d-grid justify-content-center">
        <li>Use toFixed() to round the output to 2 decimal places</li>
        <li>Display the tip amount in the output as well</li>
    </ul>
    <br>
    <h4 class="d-flex justify-content-center">2- Extend the Tip program</h4>
    <ul class="d-grid justify-content-center">
        <li>Create variables for the pre-tip total and the tip percentage</li>
        <li>Calculate the new total</li>
        <li>Output a sentence to the page - something like: “Your total bill, with tip, is £35.45”</li>
    </ul>
    <br>
    <p class="h5 d-flex justify-content-center">...Extension: round the figure to 2 DP and display the tip amount...<p>
    <br>
    <p class="h6 d-flex justify-content-center">(Below is my solution to the task. I also used boostrap to style the whole HTML document.)</p>
</div>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Programming Concepts</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
</head>
<body class="bg-dark text-light">
    <!-- Name for Programe -->
    <h1 class="container d-flex justify-content-center align-items-center text-info my-5">Tip Calculator:</h1>
    <br>
    <!-- The Function displays output here once called -->
    <p class="d-flex justify-content-center align-items-center h4" id="tipOutput">Your tip is £...</p>
    <br>
    <div class="container d-flex justify-content-center w-50 border-bottom"></div>
    <br>
    <p class="d-flex justify-content-center align-items-center h4" id="totalOutput">Your total bill, with tip, is £...</p>
    <br>
    <div class="container d-flex justify-content-center mt-5">
        <!-- Bill input field -->
        <div class="px-5">
            <label class="mb-2" for="billAmount">Bill Total:</label>
            <input class="w-100" type="text" id="billAmount" placeholder="Enter amount...">
        </div>
        <!-- Tip input field -->
        <div class="px-5">
            <label class="mb-2" for="tipAmount">Tip Percentage:</label>
            <input class="w-100" type="text" id="tipAmount" placeholder="Enter percent...">
        </div>
    </div>
    <br>
    <!-- Button to call the function -->
    <div class="d-grid gap-2 col-4 mx-auto">
        <button class="btn btn-info" id="calcBtn" type="button">Calculate</button>
    </div>
    <script src="./tipCalc.js"></script>
</body>
</html>
```

<br>

```js
// Start of my function and how its been called for
document.getElementById("calcBtn").onclick = function amountToTip() {

// Declaring variables for later use
    let tipAmount;

    let totalAmount;

// getting the values from the user that is put in the input field
    let billAmount = Number(document.getElementById("billAmount").value);
// getting the values from the user that is put in the input field
    let tipPercentage = Number(document.getElementById("tipAmount").value);

// I used an if statement to calculate and display an output to the DOM weather the user enters values or not
    if (billAmount > 0 && tipPercentage >= 0) {
        tipAmount = (billAmount / 100) * tipPercentage;
        tipAmount = Number(tipAmount).toFixed(2);
        document.getElementById("tipOutput").innerHTML = "Your tip is £" + tipAmount;
        totalAmount = Number(billAmount) + Number(tipAmount);
        totalAmount = Number(totalAmount).toFixed(2);
        document.getElementById("totalOutput").innerHTML = "Your total bill, with tip, is £" + totalAmount;
    } 
    else {
        document.getElementById("tipOutput").innerHTML = "Enter Bill amount and Percent to tip...";
        document.getElementById("totalOutput").innerHTML = " ";
    }
};
```