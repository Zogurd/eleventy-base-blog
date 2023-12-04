---
title: Function & Control Flow
description: This post is about funtion and controle flow completed via The Coders Guild.
date: 2023-11-07
tags:
---
<div class="container">
    <h4 class="d-flex justify-content-center">Task 1</h4>
    <p class="d-flex justify-content-center">Write a function that outputs a sentence. Then invoke that function later in your code.</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 2</h4>
    <p class="d-flex justify-content-center">Write a simple program to combine a first name and a last name inside a function. Then update the function to accept a first and last name as arguments.</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 3</h4>
    <p class="d-flex justify-content-center">Add a return statement to your 'name' function. Use that function to set the value of a variable.</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 4</h4>
    <p class="d-flex justify-content-center">a) Make a variable called "temperature". Write some code that tells you to put on a coat if it is below 50 degrees</p>
    <p class="d-flex justify-content-center">b) Extend the Program to show the following:</p>
        <ul class="d-grid justify-content-center">
            <li>If it's less than 50 degrees, wear a coat.</li>
            <li>If it's less than 30 degrees, wear a coat and a hat.</li>
            <li>If it's less than 0 degrees, stay inside.</li>
            <li>Otherwise, just pants and vest is fine.</li>
        </ul>
    <p class="d-flex justify-content-center">c) Add a logical operator to your ‘Shall I wear a coat?’ program</p>
    <br>
    <p class="h6 d-flex justify-content-center">(Below is my solution to the tasks.)</p>
</div>

```js
// task 1
function doSomething() {
	console.log("I'm doing something...");
};

doSomething();

// task 2 & 3
function fullName(firstName, lastName) {
	return `${firstName} ${lastName}`;
};

let myName = fullName("Ash", "Jackson");
console.log(myName);

// task 4
let temperature = prompt("Enter the temperature...");
temperature = Number(temperature);

if (temperature <= 50 && temperature >= 30) {
    alert("WEAR YOUR COAT!!!");
    console.log("WEAR YOUR COAT!!!");
} else if (temperature < 30 && temperature > 0) {
    alert("WEAR YOUR COAT AND HAT!!!");
    console.log("WEAR YOUR COAT AND HAT!!!");
} else if (temperature <= 0) {
    alert("STAY INSIDE!!!");
    console.log("STAY INSIDE!!!");
} else {
    alert(`It's ${temperature}, just pants and vest is fine.`);
    console.log(`It's ${temperature}, just pants and vest is fine.`);
};
```