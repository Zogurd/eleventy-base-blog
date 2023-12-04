---
title: Pseudocode
description: This post is about Pseudocode and why/how we use it.
date: 2023-11-25
tags:
---
<div class="container">
    <p>Pseudocode is a description of the steps in an algorithm using a mix of conventions of programming languages (like assignment operator, conditional operator, loop) with informal, usually self-explanatory, notation of actions and conditions.</p>
    <p>Although pseudocode shares features with regular programming languages, it is intended for human reading rather than machine control. Pseudocode typically omits details that are essential for machine implementation of the algorithm. The programming language is augmented with natural language description details, where convenient, or with compact mathematical notation.</p>
    <p>The purpose of using pseudocode is that it is easier for people to understand than conventional programming language code, and that it is an efficient and environment-independent description of the key principles of an algorithm.</p>
    <p>It is commonly used in textbooks and scientific publications to document algorithms and in planning of software and other algorithms.</p>
    <p>No broad standard for pseudocode syntax exists, as a program in pseudocode is not an executable program. However, certain limited standards exist (such as for academic assessment).</p>
    <h4 class="d-flex justify-content-center">How to write Pseudocode:</h4>
    <ul class="d-grid justify-content-center">
        <li>Create a statement or notation that identifies the main goal of this code.</li> 
        <li>List the steps or tasks in a logical sequence.</li>
        <li>If using loops or conditionals, indent the line of code.</li>
        <li>Use programming conventions for naming commands and appropriate formatting.</li>
        <li>As the code progresses, explain everything happening using notation.</li>
        <li>Proofread the code for clarity and ease of understanding. Make sure a client or non-technical person<br> reviewing the code can easily follow the flow and intention.</li>
    </ul>
    <br>
    <h4 class="d-flex justify-content-center">Avoid the following common mistakes while writing pseudocode:</h4>
    <ul class="d-grid justify-content-center">
        <li>Avoid using long sentences or complex language structures. Keep the code clean and simple.</li>
        <li>Work from a flowchart to ensure all steps are covered and there are no holes in the flow of logic.</li>
        <li>Keep the wording simple and follow programming structures and formatting for ease of translation.</li>
    </ul>
    <br>
    <p class="h6 d-flex justify-content-center">(Below is my example of Pseudocode aswell as some updates I added when using it to write JavaScript code)<p>
</div>

```js
// TASK ONE...

//button click to call the FUNCTION
// FUNCTION called FixStart
    // VARIABLE looking for user string input
    // convert to an array
    // FOR loop to loop through the string
        // IF string has a repeacting letter same as first letter
            // replace same letter with *
            // RETURN the new version of the sting (update: output the result to the DOM)

document.getElementById("fixStart").onclick = function FixStart() {

    let myString = document.getElementById("stringInput").value;

    let myArray = myString.split("");
    
    for (i = 1; i <= myArray.length; i++) {

        if (myArray[i] === myArray[0]) {
            myArray[i] = "*";
        }
    }
    document.getElementById("fixStartOutput").innerHTML = myArray.join("");
    console.log(myArray.join(""));
};


// TASK TWO...

//button click to call the FUNCTION
// FUNCTION called ReadingList
    // create a list of objects
        // title = string, author = string, already read = boolean
    // use a FOR loop to loop through each object
        // IF already read = true 
            // log "already read (title and author)"
        // ELSE IF already read = false
            // log "not read + (title and author)"

document.getElementById("readingList").onclick = function ReadingList() {

    const books = 
        [{
            title: "Harry Potter",
            author: "J.K Rowling",
            alreadyRead: true,
        }, {
            title: "Girl with the Dragon tattoo",
            author: "Stieg Larsson",
            alreadyRead: false,
        }, {
            title: "The Great Gatsby",
            author: "F.Scott Fitzgerald",
            alreadyRead: false,
        }, {
            title: "A Smarter Way To Learn HTML & CSS",
            author: "Mark Myers",
            alreadyRead: true,
        }, {
            title: "A Smarter Way To Learn JavaScript",
            author: "Mark Myers",
            alreadyRead: true,
        }, {
            title: "The Lord of the Rings",
            author: "J.R.R Tolkien",
            alreadyRead: true,
        }];

    let selected = document.querySelector('input[name="userInput"]:checked').value;

    let text1 = "Books I have read:"
    let text2 = "Books I haven't read:"

        for(i = 0; i < books.length; i++) {
            if (selected === "read" && books[i].alreadyRead === true) {
                document.getElementById("readingListOutput").innerHTML = text1 += "<br>" + "- " + books[i].title + " by " + books[i].author;
                console.log(`I have read ${books[i].title} by ${books[i].author}`);
            } else if (selected === "notRead" && books[i].alreadyRead === false) {
                document.getElementById("readingListOutput").innerHTML = text2 += "<br>" + "- " + books[i].title + " by " + books[i].author;
                console.log(`I haven't read ${books[i].title} by ${books[i].author}`);
            }
        };
};


// TASK THREE...

//button click to call the FUNCTION
//FUNCTION called Recipe
    // create a list of objects
        // title = string, servings = number, ingredients = array of strings, directions = string
    // use a FOR loop to loop through each object
        // IF has ingredients
        // RETURN title and ingredients

document.getElementById("recipe").onclick = function Recipe() {

    const recipies = 
        [{
            title: "Apple Crumble Sundae",
            servings: 4,
            ingredients: [" 2 tbsp Butter"," 4 green apples"," 1 tbsp ground Cinnamon"," 2 tbsp light brown sugar", " 8 scoops Vanilla ice cream", " 2 ginger nuts biscuits(crushed)"],
            directions: "STEP 1 - In a small saucepan, melt the butter over a gentle heat and add the apples, cinnamon and sugar. Cook for 10 mins or until the apples have softened but still hold their shape. STEP 2 - Split the mixture between four sundae glasses or bowls. Sit 2 scoops of ice cream on top of each, followed by the crushed biscuits. Serve while the apple mix is still warm."
        }, {
            title: "Sticky Toffee Puddings",
            servings: 4,
            ingredients: [" 4 large chocolate muffins(crumbled)"," 50g large sultanas"," small knob of butter, for greasing"," 50g light muscovado sugar", " 50g butter", " 75ml double cream", " vanilla ice cream, to serve"],
            directions: "STEP 1 - Heat oven to 200C/180C fan/gas 6. Mix the muffins with the sultanas. Divide between 4 buttered ramekins or one baking dish. Cover with foil and bake for 8 mins until just warmed through. STEP 2 - Meanwhile, place the sugar, butter and cream in a small pan and gently heat together, stirring until the sugar dissolves. Pour the sauce over the muffin mixture and serve warm with ice cream."
        }, {
            title: "Banoffee Splits",
            servings: 2,
            ingredients: [" 2 small ripe bananas"," 4 scoops ice cream"," 1 chocolate bar(chopped into small chunks)"," 3 tbsp cream", " small knob of butter"],
            directions: "STEP 1 - Tip all the sauce ingredients into a small saucepan and heat gently, stirring until you have a smooth sauce. Peel and split the bananas. Put 2 halves on each of 2 serving plates, add 2 scoops of ice cream to each plate, drizzle over the warm sauce and serve straight away."
        }];

    let text = "Recipies: "

        for(i = 0; i < recipies.length; i++) {
            if (recipies[i].ingredients != "") {
                document.getElementById("recipeOutput").innerHTML = text += "<br><br>" + "- " + recipies[i].title + ": " + recipies[i].ingredients;
                console.log(`${recipies[i].title}: ${recipies[i].ingredients}`)
            }
        };

```