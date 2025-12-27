# Exercises

The following exercises are used to test your skills when developing a client side web application with react (or preact if you prefer).

## Tasks

### 1. Profile View

You are tasked with writing an application that will be used to display a user profile. This is a typical activity for most websites that have an account system and profile page.

The profile page should display the following bits of information:

* Name, their full name, recorded as a string 

* Role, this should be either `User` or `Admin`, this should be a drop-down menu, consider using `<select>`.

* Email, recorded as a string that has only 1 `@` symbol between two words. Remember this rule when implementing a form for a simple verifier. 

* Location, keeps track of their current suburb/city and country. Record both parts as a string.

The component you are building will need to display all these elements.

Consider the following:

* What components would you create?
* What html tags would you use?
* How would you style the profile view?


### 2. Using fetch to get a profile

In exercise `#1`, you simply displayed some mock data in the view. This time, you are to use the given express server and retrieve the data from it using a `GET` request and using the function `fetch`.

The endpoint to retrieve them from is at `/profile/:userid`, where `:userid` is a place where an integer goes.

You should be able to get the records that correspond to id `1` and `2`.

Hints:

* Use fetch to retrieve the record
* Make sure you make it a `get` request
* The data is going to be in a JSON format.
* Make sure you have the server running before making the requests.

### 3. Create a profile form

As a continuation from the previous task, create a component that will allow someone to create a profile (assuming they do not have one or they are doing some amount of administration).

Using the information from the previous exercise, you will need to use the `<input>` tags along with `onChange` events to update variables when the user inputs text.

As a hint, you could call this component `CreateProfile`, make sure you include an input field for the attributes in the previous exercise and utilise the `fetch` function.

You can use the included express server to test if your data has changed when you have submitted it.

Hints:

* `fetch` is required for this task, use a `POST` method and make sure you convert the data into a JSON string.
* You do not have to handle the case for updating or deleting a profile, leave that for the next task.

### 4. Updating a profile

Modify the exercise `#2` to now contain a button to `Update` the profile. Once you have created this button, you can create a new view that will allow for updating a profile that already exists.

Make sure you use some identifiable field that would allow you to submit an update and modify the data of those fields, in addition, make sure you read the comments and documentation provided.

Hints:

* You will need to use `fetch` again here.
