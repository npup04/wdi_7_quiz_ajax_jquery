# JQuery/Ajax Quiz

Write your answer below each question.

### Question 1
(a) What is a click handler?
- a click handler is a method where we can set functionality for user input event, such as a mouse click, mouseover or mouseup action that will execute a function.

(b) Where in your JS file should you put it, and WHY?
- it should be in the document.ready section so that it will be ready for the user to use it.

### Question 2
If you get the error `$ is undefined`, what does that mean and what could you do to fix it?
- it means that the variable $ was not defined at the time it was called upon.

### Question 3
What should go in the `$(document).ready()` part of your JS file?
- anything you want to run as soon as the html document has finished loading.

### Question 4
In an AJAX GET request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent?
```
$.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
```
-once the ajax GET request is finished, return the data that was retrieved from the ajax call.

### Question 5
In an AJAX POST request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent? (Hint: it's not the same as in Question 4.)
```
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'POST',
    dataType: 'JSON',
    data: { user: { name: "Anna", about: "instructor", email: "hi@gmail.com" } },
  })
  .done(function(data) {
    console.log("success!");
  });
```
-once the ajax POST request is finished, return the object that was posted in the ajax call.

### Question 6
Suppose you had the following form in your HTML file. Use jQuery to write a single line of code that takes whatever the user entered in the textbox and saves it to the variable `user_input`.
```
  <form>
    <p>The dress is:</p><input type="text" id="color">
    <input type="submit" value="Submit" id="submit">
  </form>
```
- var user_input = $('submit').val();

### Question 7
This code looks like it works, but when you run it, you see that the `UserApp.add_all_users()` function executes but `console.log` displays `undefined`. What's wrong with the code?
```
UserApp.get_all_users = function() {
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
  UserApp.add_all_users(data);
};

UserApp.add_all_users = function(data) {
  console.log(data);
};
```
- on line 69 when add_all_users(data) is called in the get_all_users function, it is outside of the done() method so the data that was returned from get_all_users can't be passed into UserApp.add_all_users(data). Position UserApp.add_all_users(data); in line 83 will work:
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!");
    UserApp.add_all_users(data);
  });

};



