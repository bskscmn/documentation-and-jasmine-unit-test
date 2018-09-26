

# Project-8 / Openclassrooms - Frontend Developer Path  Enhance an existing project
 
Aim of the project is working on an existing codebase by fixing bugs, adding tests, and optimizing performance.

## About the Todos Application

Todos application is an online Todo list manager. 

### Features

* New Todos may easily added, and deleted.
* It allows a user to modify tasks by double clicking it.
* User can mark the task by clicking on checkbox when it is completed and unmark by second click.
* Select all arrow at the top left allows the user to mark all as completed.
* The completed tasks are marked with a tick and crossed out text.
* It allows filtering for All, Active and Completed.
* Clear Completed button lets user to clear all completed tasks.


### Architecture
**Folders**
* `js` contains source files of the javascript
* `test` contains Jasmine unit test files.
* `node_modules` contains integrated modules such as jasmine (unit testing) and todomvc (MVC framework).

**Main Javascript Files**

* `js/app.js` sets up a new Todo list.
* `js/controller.js` specifies the interactions between the view and the model.
* `js/model.js` defines data management methods
* `js/view.js` defines data displaying methods
* `js/template.js` returns a predefined template.
* `js/store.js` create a storage space on the client host.


## Step 1: Fix the bugs

### Manual bug fixing. 

#### 1. `js/controller.js` (line 95)

> ~~Controller.prototype.adddItem~~

Fixed:

> Controller.prototype.addItem

#### 2.	`store.js` (line 83)

```
// Generate an ID 
var newId = ""; 
var charset = "0123456789";

for (var i = 0; i < 6; i++) {
  newId += charset.charAt(Math.floor(Math.random() * charset.length));
}
 ```
Fixed:
```
// Generate an ID checking if it is unique
var newId = ""; 
var charset = "0123456789";

var duplicatedID = true;

while (duplicatedID){
  for (var i = 0; i < 6; i++) {
    newId += charset.charAt(Math.floor(Math.random() * charset.length));
  }
  duplicatedID = false;
  for (var i = 0; i < todos.length; i++) {
    if (todos[i].id == newId) {
      duplicatedID = true;
    }
  }
}
 ```
Another fix for unique id could be:

`var newId = new Date().getTime();`

#### 3. `index.html` (line 16);
```
<input class="toggle-all" type="checkbox">
<label for="toggle-all">Mark all as complete</label>
```
Fixed:
```
<input id="toggle-all" class="toggle-all" type="checkbox">
<label for="toggle-all">Mark all as complete</label>
```
## Step 2: Add tests

#### Jasmine unit testing

Added some tests to already written ones.

1.	should show entries on start-up
2.	should show all entries without "all" route
3.	should show active entries
4.	should show completed entries
5.	should show the content block when todos exists
6.	should highlight "All" filter by default
7.	should toggle all todos to completed
8.	should update the view
9.	should add a new todo to the model
10.	should remove an entry from the model

![Test Results](https://github.com/bskscmn/todolist_docs/blob/master/documents/jasmine.jpg?raw=true)

Audit Performance

-	page loads fast, because it based only on html, css and vanilla.js technologies,
-	page doesn’t need a large amount of memory, because it doesn’t require any media files,
-	application is simple, without any heavy fonts, animations or complicated styles to be load.

#Audit a competitor site: http://todolistme.net


