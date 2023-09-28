Try to connect React & Redux app to API
Learning objectives
Connect an existing API via Redux and use the data to display something in a UI.
Estimated time: 1h
Exercise
This exercise will help you learn how to connect async logic to interact with a Redux store when fetching data from an external API.

IMPORTANT NOTE: Read all instructions before you start this exercise.

Instructions
You will be working with the following external API: Random User API.

Create a new React application using Create React App
Install @reduxjs/toolkit react-redux
Create a new Redux store and connect it to your React application
Use configureStore and pass it an object with a reducer, which should take users reducer
Export your store as default
Import and wrap <Provider> in your top-level component and inject your store
Create a new slice of state in src/store/users/usersSlice.js
Use createSlice and define:
name as a string
initialState, which includes users as an array, isLoading as a boolean and error as undefined
extraReducers as an empty object
Export your reducer from your slice
Export the slice itself as default
Import the usersSlice into your store and assign it to your reducer object
Create a new component that will contain your fetched users:
Import useSelector and destructure your users, isLoading and error from your users state
Add a loading state; JSX content that shows when isLoading is true
Add an error state; JSX content that shows when error has received new content
Add a default state that maps over your users inside of an unordered list:
Add a key to the container element.
Render the first and last name of the user
At this stage, you should have successfully implemented Redux Toolkit! If not, please go back to the previous steps

Inside of src/users/usersSlice.js, create an action creator that fetches your users:
Import createAsyncThunk and instantiate it in a new variable
Pass your action creator 2 arguments: an action type and an asynchronous function (use the documentation)
Write your fetching logic inside of a try/catch block:
In the try block, return your fetched data
In the catch block, pass your error to the rejectWithValue
Inside of your userSlice variable, modify the extraReducers:
Replace the empty object with a function that takes 1 argument, builder
Add 3 cases with addCase, which takes 2 arguments: an action type and a reducer function
In the pending state, mutate the isLoading state to true
In the fulfilled state, mutate the isLoading state to false and assign the payload to the users state
In the rejected state, mutate the isLoading state to false and assign an error message to the error state
Back in your new component, add the following changes:
Import useDispatch and instantiate it inside of a variable within the component
Import useEffect and pass it 2 arguments: an empty function and an empty dependency array
Import your action creator and dispatch it inside of your useEffect. Be sure to add the action creator to the dependency array
Test to see if everything works. You should now have a working application!