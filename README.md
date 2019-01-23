## Instructions

You will be building out the following App:
![tea gif]()


-- As a user, when the page loads, I should see a list of bubble teas retrieved from an API.

-- As a user, clicking the 'Save' button of any bubble tea will save any changes to the description to the database

-- As a user, clicking the 'Delete' button of any bubble tea will remove the tea from the database


## The API

Instead of actually accessing the data from a remote API, this challenge uses a package called [json-server](https://github.com/typicode/json-server) to create a fake API for development and testing.

It is very easy to set-up.

1 - Run the command `npm install -g json-server` in the command line from this directory

2 - Run `json-server --watch teas.json`

That's it. You will have a server running on `localhost:3000` that serves the JSON data contained in the `teas.json` file.

*Troubleshooting: If this fails, be sure you don't already have something running on port 3000*

## Deliverables and How to Approach

For this challenge, it is important to work iteratively, one feature at a time, before moving on to the next. You should **prioritize making code that works over attempting all of the deliverables.**

### Step 1 - Display All Teas

When the page loads, I should see a list of all of the teas rendered onto the page as rectangular cards. Each card should display information including the tea's name, an image of the tea, and the description of the tea retrieved from the API. The endpoint we need to retrieve all the teas is a conventional RESTful route.

* **Route:** GET `http://localhost:3000/teas`

#### Styling

**One important point** is that for the tea cards to show up correctly, the html should have the following class names:

```html
<div id="tea-container" class="container">
   <div class="card">
     <h5>Tea Name</h5>
     <img src="...">
     <textarea>The tea's description goes here</textarea>
     <button>Save</button>
     <button>Delete</button>
   </div>
<div>
```


### Step 2 - Edit Tea Details

Clicking the 'Save' button will save any changes made to the description to the database for that particular tea and the changes should persist. For example, if I update the details of "Long Island Tea" then refresh the page, the textarea should show the updated description.

To update a tea you'll need to make a PATCH request
* **Route:** PATCH `http://localhost:3000/teas/:id`
* **Body:**
```js
  {description: "your new description"}
```
* **Headers:**
```js
  {
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  }
  ```

  **Important Notes:**
  * For all intents and purposes, PATCH behaves the same as POST. If you know how to POST, you know how to PATCH
  * When using `fetch` to make a PATCH request, be sure to capitalize method: 'PATCH'


### Step 3 - Delete a Tea

Clicking the 'DELETE' button will remove the particular tea from the database and the changes should persist. For example, if I delete "Long Island Tea" then refresh the page, I should no longer see that tea.

To update a tea you'll need to make a PATCH request
* **Route:** DELETE `http://localhost:3000/teas/:id`

## Considerations

You are free to solve this in any way you choose. It is not required that you have ES6 classes or use Object Orientation. We would recommend beginning with a straightforward functional implementation and refactoring to objects as needed.
