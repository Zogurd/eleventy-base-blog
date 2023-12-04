---
title: Loops, Arrays & Objects
description: This post is about JavaScript loops, arrays and objects.
date: 2023-12-01
tags:
---
<div class="container">
    <h4 class="d-flex justify-content-center">Task 1</h4>
    <p class="d-flex justify-content-center">Write a loop that outputs the 7 times table, from 7 x 1 = 7 to 7 x 12 = 84<br>(Bonus: use nested loops and print all the times tables from 1 - 12)</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 2</h4>
    <p class="d-flex justify-content-center">Create an array of your favourite foods and print some of them to the screen</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 3</h4>
    <p class="d-flex justify-content-center">Use a for loop to print a list of all your favourite foods</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 4</h4>
    <p class="d-flex justify-content-center">Create an object to hold information on your favourite recipe. Then display the properties on screen. (Bonus Points: Create a loop to list all the ingredients and directions.)</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 5</h4>
    <p class="d-flex justify-content-center">Add a function called letsCook and have it say: "I'm hungry! Let's cook..." with the name of your recipe title. Call your new method.</p>
    <br>
    <p class="h6 d-flex justify-content-center">(Below is my solution to the tasks in JavaScript)</p>
</div>


```js
// Pre-Task code with for loop and while loop
    // Pre-task For loop
        document.getElementById("preTaskFor").onclick = function() {
            let preTaskForOutput = [];
            for (let i = 1; i <= 12; i++) {
                preTaskForOutput.push(i);
                console.log(i);
            };
            document.getElementById("preTaskForOutput").innerHTML = preTaskForOutput; 
        };
    // Pre-task while loop 
        document.getElementById("preTaskWhile").onclick = function() {
            let myNum = 1;
            let preTaskWhileOutput = [];
            while (myNum <= 12) {
                preTaskWhileOutput.push(myNum);
                console.log(myNum); 
                myNum = myNum + 1;
            };
            document.getElementById("preTaskWhileOutput").innerHTML = preTaskWhileOutput;  
        };


// Task 1 code with for loop and while loop
    // Task 1 for loop
        document.getElementById("task1For").onclick = function() {
            let task1ForOutput = [];
            for (let x = 1; x <= 12; x++) {
                task1ForOutput.push(`<br>The ${x} times table:`);
                console.log(`The ${x} times table:`);
                for (let j = 1; j <= 12; j++) {   
                    task1ForOutput.push(`<br>${x} × ${j} = ${x * j}`);
                    console.log(`${x} × ${j} = ${x * j}`);
                }	
            }
            document.getElementById("task1ForOutput").innerHTML = task1ForOutput;
        };
    // Task 1 while loop
        document.getElementById("task1While").onclick = function() {
            let firstNum = 1;
            let secondNum = 1;
            let task1WhileOutput = [];
            while (firstNum <= 12) {    
                task1WhileOutput.push(`<br>The ${firstNum} times table:`);
                console.log(`The ${firstNum} times table:`);
                while (secondNum <= 12) {
                    task1WhileOutput.push(`<br>${firstNum} × ${secondNum} = ${firstNum * secondNum}`);
                    console.log(`${firstNum} x ${secondNum} = ${firstNum * secondNum}`);
                    secondNum++;   
                };
                secondNum = 0;
                firstNum++;
            };
            document.getElementById("task1WhileOutput").innerHTML = task1WhileOutput;
        };


// Task 2 code with for loop and while loop
        const favFoods = ["chicken", "fish", "olives", "yoghurt", "chocolate"]; //global so other functions can access data
        document.getElementById("task2").onclick = function() {
            document.getElementById("task2Output").innerHTML = `${favFoods[1]}, ${favFoods[2]}`
            console.log(`${favFoods[1]}, ${favFoods[2]}`);
        };


// Task 3 code with two different for loops
    // Task 3 first type of for loop
        document.getElementById("task3For").onclick = function() {
            let task3ForOutput = [];
            for (let z = 0; z < favFoods.length; z++) {
                task3ForOutput.push(` ${favFoods[z]}`);
                console.log(favFoods[z]);
            };
            document.getElementById("task3ForOutput").innerHTML = task3ForOutput;
        };
    // Task 3 second type of for loop
        document.getElementById("task3OtherFor").onclick = function() {
            let task3OtherForOutput = [];
            for (const food of favFoods) {
                task3OtherForOutput.push(` ${food}`);
                console.log(food);
            };
            document.getElementById("task3OtherForOutput").innerHTML = task3OtherForOutput;
        };


// Task 4/5 code with for loop and while loop
        document.getElementById("task45For").onclick = function() {
            //variables used to collect data that will be outputed to the DOM
            let cookFunc;
            let titleAndServings;
            let theIngredients;
            let ingredientsList = [];
            let theDirections;
            let directionsList = [];
            
            const favRecipe = {
                letsCook () {
                    cookFunc = `I'm hungry! Lets cook ${favRecipe.title}!`;
                    console.log(`I'm hungry! Lets cook ${favRecipe.title}`);
                },
                title: "Apple Crumble Sundae",
                servings: 4,
                ingredients: [
                    " 2 tbsp Butter",
                    " 4 green apples",
                    " 1 tbsp ground Cinnamon",
                    " 2 tbsp light brown sugar",
                    " 8 scoops Vanilla ice cream",
                    " 2 ginger nuts biscuits(crushed)"
                ],
                directions: [
                    "STEP 1 - In a small saucepan, melt the butter over a gentle heat and add the apples, cinnamon and sugar. Cook for 10 mins or until the apples have softened but still hold their shape.", 
                    "STEP 2 - Split the mixture between four sundae glasses or bowls. Sit 2 scoops of ice cream on top of each, followed by the crushed biscuits. Serve while the apple mix is still warm."
                ]
            };
            favRecipe.letsCook()

            titleAndServings = `${favRecipe.title} (for ${favRecipe.servings}):`;
            console.log(`${favRecipe.title} (for ${favRecipe.servings})`);

            theIngredients = '<br>Ingredients:<br>';
            console.log('Ingredients:');
            for (const ingredient of favRecipe.ingredients) {
                ingredientsList.push(ingredient);
                console.log(ingredient);
            }

            theDirections = '<br>Directions:<br>';
            console.log('Directions:');
            for (const direction of favRecipe.directions) {
                directionsList.push(direction);
                console.log(direction);
            };
            document.getElementById("task5ForOutput").innerHTML = `${cookFunc}`;
            document.getElementById("task4ForOutput").innerHTML = `${titleAndServings} <br>${theIngredients} <br>${ingredientsList} <br>${theDirections} <br>${directionsList}`;
        };
```