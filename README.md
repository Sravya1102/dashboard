## Running the code
1. `npm install`
2. `ng serve`
3. view at localhost:4200

## Overview
This repo a simple web app.

The three main aspects of this web app are to demon: [see Implementation Notes](#implementation-notes)

1. API Management
2. State management & storage
3. UI/UX (styling code management)

The solution is purely a front-end solution

The solution has been developed using a mock API, provided by: [https://jsonplaceholder.typicode.com](https://jsonplaceholder.typicode.com)

## Requirements

### 1. Login Page

- Used the GET users endpoint [https://jsonplaceholder.typicode.com/users](https://jsonplaceholder.typicode.com/users)
- The "login" is just the user entering the email address
  - User is logged in if the email address is found in the `/users` API
  - Upon failed login (email not found), display an error message
- After successful login, user will be in a "logged in state"
  - Show "To Do" page as the landing page

### 2. Navigation Bar (after login)

Once a user is logged in, there will be a persistent navigation bar.

- Navigation links to the todo page and the posts page
  - "Posts" link on click should show a pop up saying "This page is not available"
  - The button linking to the todo page should have a number next to it that represents the number of incomplete todos ie TODOs (5)
- Display the user’s name with hyperlink to website (Company’s name), example: Leanne Graham (Romaguera-Crona) 
- A button to log out
  -  On click, the user should be returned to the login screen

### 3. To Do Page
  
  1. The “To Do” link on the navigation is highlighted
  2. Display list of To Dos (titles) for the user as checkboxes
      - a. If completed = false - the checkbox should be unchecked and the text
        should be red
      - b. If completed = true - the checkbox should be checked and the text should
        be green
  3. In addition to the data provided by the API, the state should also store a
    “completedDate” field as part of the “To Do” item
      - a. If completed = false - the completedDate should be null
      - b. If completed = true - generate a random or hard coded data in the past
  4. When the user clicks on an already checked box (completed item)
      - a. Modify the state of the to do item to set completed = false and
        completedDate = null
  5. When the user clicks on an unchecked box (non-completed item), modify the
    state of the to do item to set:
      - a. completed = true
      - b. completedDate = {currentDate}
  6. Make the following filters available to the user:
      - a. Show all
      - b. Show completed
      - c. Show completed today - display completed task with date of today
      - d. Show incomplete


## Implementation Notes

### API Management

The data loading has been structured so that calls to the API are minimized. A [helper service](src/app/api/api.service.ts) has been configured with all the CRUD functions. The functions to access the api aree added to `api.service.ts`.

### State Management & Storage

The main point of emphasis of this app is to demonstrate the ability to manage state efficiently.

#### NGXS

The documentation for ngxs can be found [here](https://www.ngxs.io/).

Two NGXS states have been configured, [user.state](src/app/store/user.state.ts) and [todo.state](src/app/store/todo.state.ts), along with sample action classes in the same directory.

#### Models

There are a couple of model files in the [models](src/app/models/) directory. 

#### User State

[The user state](src/app/store/user.state.ts) holds information about the logged in user. The actions to mutate this state are added [here](src/app/store/user.action.ts)

#### Todo State

[The todos state](src/app/store/todo.state.ts) holds information about the list of todos. The actions to mutate this state are added [here](src/app/store/todo.action.ts)
