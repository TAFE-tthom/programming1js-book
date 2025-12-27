# Exercises

The following exericses are a good challenge and demonstration of your skills of using all tools and skills documented in the chapter.

## Tasks

### 1. TodoList

Write a website that will allow someone to construct a TODO List website, it must have:

* A component that allows someone to enter, the user should be able to click a button and add the task to an existing table
  * Task name
  * Task description
  * Date it needs to be done by

* Tasks should be editable with their controls hidden until an EDIT button is clicked by the user, the user should be able to edit the contents of the task

* There should be a delete button for the task to remove it from the table


### 2. Image Gallery

Write a website that will be an image gallery, the user should be able to have their cursor hover over images and let have more of a preview. When the image is clicked, the image should enlarge to fill the browser window.
 
* Your image gallery should also handle key events, when the user presses left or right arrow keys on the keyboard, it should switch to a new image

* Add keyboard events to your image gallery from last week's exercises. Make sure it changes the image to be the next image in the gallery itself. Check the images within the gallery element.


### 3. Tic-Tac-Toe (Naughts and Crosses)

This will be a combination of using HTML, CSS and Javascript.
 
Create 3 rows with 3 cells each of empty boxes. Size them appropriately.
* Simple method would be to size it as 50px each
* Consider putting the game inside a container to maintain the size and ensure that you can create rows.
 
As an extension: Allow your elements to be resizable to the browser window. You may need to consider 'stretch'ing your images or using an svg.
 

Afterwards, Add an onclick event to each element, this event should check
to see if it is currently empty, if so:
 
* Allow a X or an O to be placed here and move to the next player's turn
 
If it is not empty:
 
* Reject the move, you can provide an alert to the user that they have made an invalid move.
 
For each event, it should check to see if the game is complete, this is a matter of seeing if there is a Row, Column or Diagonal that are all of the same symbol (X or O).
 
Your website should declare the winner (either with an alert or update to another HTML element).
 
At the end of this, add a reset button to reset the game to the beginning. Clearing the board for a new game.
