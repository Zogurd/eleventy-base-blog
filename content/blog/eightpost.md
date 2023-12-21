---
title: The DOM part 2
description: This post is about The DOM.
date: 2023-12-21
tags:
---
<div class="container">
    <h4 class="d-flex justify-content-center">Task 1</h4>
    <p class="d-flex justify-content-center">Go to codepen.io/andrushka/pen/rNdQmOd, Pick 4 animals. Go to pexels.com and get 4 pictures of each animal (16 total). Create a HTML page containing a search input, 4 buttons (one for each animal), 1 more button labelled “Show All”. Give each button a class of “buttonFilter”. Add 16 containers with the animal images randomly spread out. Add a class that represents the animal class=”tiger”.</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 2</h4>
    <p class="d-flex justify-content-center">Add a second class to each container that is called “imageFilter”. Add an attribute to each button animal =”tiger” (Show all, animal =”all”). Add a variable const button = document.querySelectorAll(".buttonFilter");. const images = document.querySelectorAll(".imageFilter");</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 3</h4>
    <p class="d-flex justify-content-center">Loop through each button in the button array. Add an event listener for each button that looks for a click event. Grab the animal attribute with animal = this.getAttribute("animal");</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 4</h4>
    <p class="d-flex justify-content-center">Loop through each item in the images array, If animal = all change all of the containers to display:block, If animal = “tiger” then if the container contains the class tiger display:block otherwise display:none.</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 5</h4>
    <p class="d-flex justify-content-center">Add a keyup event to the search box. The text entered should be used to filter based on the image alt attribute (or use the src attribute if you have no alts). The selected filter button should also be taken into account.</p>
    <br>
    <h4 class="d-flex justify-content-center">Task 6</h4>
    <p class="d-flex justify-content-center">Add CSS classes that show which filter is currently selected by adding a border to the clickable element. Add some helper text above the images that says something like “showing animals that match the search “{searchString}” and the filter {filter}</p>
    <br>
    <p class="h6 d-flex justify-content-center">(Below is my solution to the tasks in JavaScript)</p>
</div>

```js
const images = document.getElementsByClassName('imageFilter');
// Get the form by ID from the live collection 'document.forms'.
const form = document.forms.filters;
// Get the radio elements by name from the live collection 'form.elements'.
const animalRadios = form.elements.animalType;
// Get the search text field by name from the live collection 'form.elements'.
const search = form.elements.search;
// Get the summary element (for "showing animals that match...").
const summary = document.getElementById('summary');

function showImage(image) {
    // Get the currently selected animal from the animal type radios collection.
    const selectedAnimal = animalRadios.value;
    // If 'Show All' isn't selected, and the currently selected animal doesn't
    // match the current image's 'animal' attribute, then it shouldn't be visible.
    if (selectedAnimal !== 'all' && selectedAnimal !== image.getAttribute('animal')) {
        return false;
    }
    // At this point we know the animal isn't filtered out by the radio buttons.
    // So if there's nothing in the search text field, it should be visible.
    if (!search.value) {
        return true;
    }
    // At this point we know there's something in the search text field. If the
    // image's alt attribute includes the search value, then the image should be
    // visible; otherwise it shouldn't.
    // For a case insensitive match, convert both the alt text and the search query
    // to lower case.
  return image.alt.toLowerCase().includes(search.value.toLowerCase());
}

function filterAnimals() {
    for (const image of images) {
        if (showImage(image)) {
            image.classList.remove('hidden');
        } else {
            image.classList.add('hidden');
        }
    }  
}

function updateSummary() {
    const filterLabel = form.querySelector(`label[for=${animalRadios.value}]`).textContent;
    summary.textContent = search.value ?
        `Showing animals that match the filter "${filterLabel}" and the search "${search.value}".` :
        `Showing animals that match the filter "${filterLabel}".`;
}

// Now update the summary on page load for the default selection.
updateSummary();

function update() {
    filterAnimals();
    updateSummary();
}

// Prevent submission of the form.
form.addEventListener('submit', (e) => {
    e.preventDefault();
});

// When an animal type is selected via the radio buttons, run filterAnimals.
for (const animalRadio of animalRadios) {
    animalRadio.addEventListener('change', update);
}

// When the search query in the search text field changes run filterAnimals.
search.addEventListener('keyup', update);
```