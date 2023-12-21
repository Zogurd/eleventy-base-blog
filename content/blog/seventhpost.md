---
title: The DOM
description: This post is about The DOM.
date: 2023-12-14
tags:
---
<div class="container">
    <h4 class="d-flex justify-content-center">Task 1</h4>
    <p class="d-flex justify-content-center">Go to the codepen. Look through the HTML first. Then try to update the JS so it sets the variables from the DOM.</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 2</h4>
    <p class="d-flex justify-content-center">Go to the codepen. Fill in the body of createElement() first. Now follow the instructions at the end and insert newElement into the DOM.</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 3</h4>
    <p class="d-flex justify-content-center">Go to the codepen. Remove the list item elements using Element.remove().</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 4</h4>
    <p class="d-flex justify-content-center">Go to the codepen. Add a submit handler to the form.</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 5</h4>
    <p class="d-flex justify-content-center">Go to the codepen. Add a submit listener to the form that prevents default. Confirm the form can’t be submitted. Add a click listener to the todo note that removes it.</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 6</h4>
    <p class="d-flex justify-content-center">Putting it all together. Follow the codepen!</p>
    <br>
    <p class="h6 d-flex justify-content-center">(Below is my solution to the tasks in JavaScript)</p>
</div>

```js
  // Store the URL of an image for each priority level.
const priorityImages = {
  low: 'https://cdn1.iconfinder.com/data/icons/prettyoffice8/256/Flag-green.png',
  medium: 'https://cdn1.iconfinder.com/data/icons/prettyoffice8/256/Flag-yellow.png',
  high: 'https://cdn1.iconfinder.com/data/icons/prettyoffice8/256/Flag-red.png',
};

// Get the form by ID from the forms collection.
const form = document.forms.todo;
// Get the todo pane (the 'ul' element) to insert todos into.
const todoPane = document.getElementById('todo-pane');
// Get the text input for the title. We'll read from this when creating the todo.
const titleInput = form.elements.title;
// Get the priority select element. We'll ready from this when creating the todo.
const prioritySelect = form.elements.priority;
// Get a *live* list of all elements with the 'todo' class.
const allTodos = document.getElementsByClassName('todo');


// Add an event listener that will
form.addEventListener('submit', function (event) {
  // First remove the 'just-created' class from all existing todos.
  for (const todo of allTodos) {
    todo.classList.remove('just-created');
  }
  // 1. Create a new todo. The details should come from the form.
  const newTodo = createTodo(titleInput.value, prioritySelect.value);
  // 2. Insert it into the DOM.
  todoPane.appendChild(newTodo);
  // 3. Clear the title input ready to create a new todo note.
  titleInput.value = '';
  // 4. Prevent the default behaviour (ie don't submit to a server).
  event.preventDefault();
});

/**
 * Creates and returns a new todo element.  
 * @param {string} title - The title of the todo
 * @param {string} priority - The priority: 'high', 'medium', 'low'.
 * @return {HTMLElement} The new todo element with 'just-created' class.
 */
function createTodo(title, priority) {
  // Create the text node with the variable 'title'.
  const textNode = document.createTextNode(title);
  // Create a div to contain the title text.
  const textDiv = document.createElement('div');
  // Add the title text to its div container.
  textDiv.appendChild(textNode);
  // Create the new list item for the new todo.
  const todo = document.createElement('li');
  // Create the new image for the todo flag.
  const image = document.createElement('img');
  // Set the src of the image to the appropriate flag.
  image.src = priorityImages[priority];
  // Add the image as the first child of the new todo.
  todo.appendChild(image);
  // Add the text div as the second child of the new todo.
  todo.appendChild(textDiv);
  // Add the standard 'todo' class and also a 'just-created' class that will be removed later.
  todo.classList.add('todo', 'just-created');
  // Add a click handler to the todo, so you can remove it by clicking.
  todo.addEventListener('click', function (event) {
    event.currentTarget.remove();
  })
  return todo;
};
```