# Exercise: Recreate the Todo list application with React

## Learning Goals

Upon completing this exercise, you will be able to:

- Manage complex state with React Hooks
- Work with array and object manipulation in JavaScript/React
- Handle form submission and user input
- Implement search and filter capabilities
- Practice component composition
- Use conditional rendering

## Introduction

You’ve had your pleasure implementing a Todo list App already using regular JavaScript with the Document Object Model (DOM) API. We’re sure you still remember how We're sure you still remember how challenging yet rewarding it was to manipulate the DOM directly. 

Now, it's time to level up and recreate this application using React. 

It is important that you follow the exercise instructions by the letter, and do not deviate from the requirements. You’ll use your base that you build now throughout the remaining bootcamp and enhance the Todo app with additional functionality later.

But why a Todo list again?

We want you to experience first-hand the gains you made in your programming journey. By recreating a familiar application with a new technology, you'll be able to directly compare the development process and see how React simplifies many aspects of web development.

This exercise will solidify your understanding of React fundamentals and prepare you for more advanced concepts. Plus, it's always satisfying to see how much more efficiently you can build something the second time around!

Are you ready?

## Getting Started

Follow these steps below:

1. Fork this Repository
2. Clone the Repository to your Computer
3. Open the Repository in VS Code
4. Open the terminal and run `npm install`
5. Run `npm run dev`
6. Follow the instructions below

## Instructions

Before you begin your exercise, we‘d like you to revisit the “Thinking in React” lesson, and re-read it. If you finished that, take a look at the following example of the todo list app:

[https://todolist.codewith.codeverge.de/](https://todolist.codewith.codeverge.de/)

This example App showcases the key features we want you to implement in your React version. Take some time to explore its functionality, paying attention to how tasks are added, marked as complete, filtered, and searched. 

> [!WARNING]  
> The `category` of each todo item is optional and can be ignored (unless you want the extra challenge)

> [!NOTE]  
> You don’t need to use the same UI! It’s just an example to make it easier for you in the first place.

Once that’s done, you can start working on the exercise, and choose you poison on how to style your React App. Choose between the different Styling approaches we’ve covered so far. fit’s important you stick to one approach and try to master the bits and bolts of the approach.

Final 2 cents before you begin: We’ve prepared a couple of todos in an array inside the `App.js` component. We’d like you to keep the object structure for each todo as it is. We’ll work upon that structure and want to have a stable API to work with.

Good luck.

### Task 1: Basic Todo List Display

Start by creating a basic todo list that displays the initial todos. Create a component that renders each todo item, displaying its name and completion status. Ensure that the list is responsive and visually appealing. Remember to use the provided todo structure in the `App.js` file as you build out this component.

### Task 2: Toggle Todo Status

Implement the ability to toggle the completion status of each todo item. Add a checkbox to each todo that, when clicked, changes the todo's status from incomplete to complete or vice versa. 

### Task 3: Adding New Todos

Create a form or input field that allows users to add new todos to the list. When a new todo is submitted, it should be added to the list of todos and displayed immediately. Ensure that the input field is cleared after submission. Remember to validate the input to prevent empty todos from being added.

### Task 4: Update Existing Todos

Add the ability to update existing todos. This could be implemented as an edit button next to each todo item. When clicked, it should allow the user to modify the todo's text. Ensure that the updated todo is immediately reflected in the list. Consider adding validation to prevent users from saving empty or duplicate todos.

### Task 5: Delete Todos

Implement a delete functionality for todos. Add a delete button or icon next to each todo item. When clicked, it should remove the corresponding todo from the list. Ensure that the deletion is reflected immediately in the user interface.

### Task 6: Separate Lists

Create separate lists for completed and incomplete todos. Implement a button that allows users to switch between only completed todos, or only incomplete todos. Ensure that the user interface clearly indicates which view is currently active and updates dynamically as todos are added, completed, or deleted.

### Task 7: Search Functionality

Implement a search functionality that allows users to find specific todos based on their text content. Add a search input field at the top of the todo list. As the user types, the list should dynamically update to show only the todos that match the search query. Ensure that the search is case-insensitive and works across both completed and incomplete todos.

## Submission

When you’ve completed the exercise:

1. Push your code to GitHub:

```bash
git add .
git commit -m "Completed Todo App with React exercise"
git push origin main
```

2. Create a Pull Request and submit your assignment.

## Bonus Challenges

If you finish early, or you want to push your skills further, here are some bonus challenges to explore:

### Task 8 (optional): Category Management

Implement a category system for todos. Allow users to create, edit, and delete categories. Each todo should be assignable to a category.

### Task 9 (optional): List View / Group by Category

Add a new view option that groups todos by category. Implement a toggle or dropdown that allows users to switch between the standard list view and the category-grouped view. In the grouped view, todos should be organized under their respective category headers. Ensure that the grouping updates dynamically as todos are added, edited, or deleted.

### Task 9 (optional): Local Storage

Implement local storage functionality to persist todos between browser sessions. When the user adds, edits, or deletes a todo, save the updated todo list to local storage. On page load, retrieve the saved todos from local storage and display them. 

## Questions and Answers

<details>
<summary>What’s the best way to generate unique IDs?</summary>

There are several ways to generate unique IDs in JavaScript for your React todo app. One way is to use the build-in `crypto.randomUUID()`.  Alternatively, you can create a simple function that combines a timestamp with a random number, like: 

```jsx
function generateId() {
    return Date.now().toString(36) + Math.random().toString(36).substr(2, 5);	
}
```

This method is generally sufficient for client-side ID generation in most todo list applications.

</details>

<details>
<summary>How can I efficiently filter and search todos?</summary>

To efficiently filter and search todos, you can use JavaScript's array methods like `filter()` and `includes()`. 

For searching, you can use the `filter()` method with a condition that checks if the todo's text includes the search query. Here's a basic example:

```jsx
    const searchTodos = (todos, query) => {
      return todos.filter(todo => 
        todo.text.toLowerCase().includes(query.toLowerCase())
      );
    }
```

These function can be called whenever the filter or search criteria change, updating the displayed todos accordingly.

It’s recommended to use use the  `toLowerCase` utility function because it ensures case-insensitive comparison. This approach makes the search more user-friendly, as it will match todos regardless of how the user or the todo text is capitalized. Additionally, performing the lowercase conversion on both the search query and the todo text improves the consistency and reliability of the search functionality.
</details>
    
<details>
<summary>What’s the best practice for updating nested state?</summary>
    
When updating nested state in React, it's important to maintain immutability. 

The best practice is to use the spread operator (`...`) to create a new copy of the state object and then update the specific nested property. 

For example, if you have a todo object within an array of todos, you might update it like this:

```jsx
    setTodos(prevTodos => prevTodos.map(todo => 
      todo.id === updatedTodoId ? { ...todo, ...updatedProperties } : todo
    ));
```

We’ve covered working with Arrays and Object Literals in full detail in the Lesson “Using useState”. If you need a refresher, please refer back to that lesson.

</details>