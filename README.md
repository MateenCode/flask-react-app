# Flask / React App

##### Requirements

1. Set up a new react app with create-react-app
1. Have your react app fetch the data from the "index" route in your flask app that you created, and render the data out in a list
1. Have your react app submit a form that makes a post request to your flask app that will create your resource

<details>
  <summary>Click for hints - Setup</summary>

- Create a component called `DogContainer`.
- It will have a `dogs` array in state. A `Dog` is an object with name (string), age (number), and breed (string).
- Render `DogContainer` in `App`
</details>

<details>
  <summary>Click for hints - Read</summary>

- Create a `DogList` component that renders inside of `DogContainer`.
- Once you have it showing up, make an AJAX request to your flask server to populate your dogs state.
- Pass the dogs to DogList from state and make it render the list of dogs in some kind of nice way.
- When it works, commit!
</details>

<details>
  <summary>Click for hints - Create</summary>

- Create a `DogNewForm` class component that lets users enter dog info. Verify that the inputs are controlled by logging state in `render()`. Test it, and when you know it works, commit.
- Make a `handleSubmit` function in `DogNewForm` that just logs `"handleSubmit in DogNewForm called"` and have it called when the form is submitted. You should see that log in the console--don't forget to `preventDefault()`. When it works, commit.
- In `DogContainer`, make a function `addDog()` that just logs "addDog" and pass it through props to `DogNewForm`. Make it so that clicking submit on dog form causes "addDog" to log. When it works, commit.
- Make `addDog` actually make an AJAX request to create a new Dog on your server. Refresh the dog list to show the newly added data.
- When it works, commit.
</details>

### Part Two

##### Requirements

1. Create a form that that is pre-filled and will make a put request to update a dog resource
1. Have your react app submit a delete request to your flask app from an "onclick" event that will send the ID of the resource you want deleted on the flask app

<details>
  <summary>Click for hints - Delete</summary>

- Create a Delete button next to each dog in your list. Make it so that it logs the ID of the dog whose delete button the user clicked by calling a method passed down through props and attached to the button. You don't necessarily need forms here, but there are a couple of different patterns for getting that ID into the delete method. Commit when you see the ID in the console.
- Make your `deleteDog` function actually make a request to delete the dog on your server. Commit when it works.
</details>

<details>
  <summary>Click for hints - Update</summary>

- Add an Edit button next to each dog in your list. Make it so that it logs the ID of the dog whose edit button the user is clicking by calling a method (`editDog`) passed down through props and attached to the button. Commit when you see the ID in the console.
- Have a value in state of `DogContainer` called `idOfDogToEdit` initialized to -1. Later, this will represent a dog currently being edited, and be used to conditionally hide and show an edit form, but for now just have your editDog button set the value of `this.state.idOfDogToEdit` using setState. Test by logging and/or using React Dev tools, and commit when it works.
- Create a `DogEditForm` component that renders in `DogContainer` when the value of `this.state.idOfDogToEdit` is something other than `-1`. Commit when you have it so that clicking any edit button makes the form show.
- Have another property in state called `dogCurrentlyBeingEdited` initialized to `null`. Make `editDog` also copy the properties of the dog currently being edited into a new object stored there in state. Test by logging and/or using React Dev tools, and commit when it works.
- Pass those values down into `DogEditForm` via props so they actually show up in the form. Commit when it works.
- Write a `handleEditChange` function in `DogContainer` that will be passed to `DogEditForm` through props and added as an onChange handler to the inputs in the edit form. That function should update the appropriate property in `dogCurrentlyBeingEdited`, which should mean that the user can type into the edit form. Commit when youhave verified that the values in state are actually being updated when the user types.
- Create a function `updateDog` in `DogContainer`. Commit after each of the following:
_ `updateDog` passed into `DogEditForm` via props and logs "updateDog" when update is clicked
_ `updateDog` actually sends an AJAX request to update the dog on your server (should be reflected on the screen)
_ `updateDog` closes the editModal
_ `updateDog` resets other edit-related state properties to their initial values
</details>

### Part Three

##### Requirements

1. Set up register and login
1. Require users to be authenticated before editing data on your server

<details>
  <summary>Click for hints - Authentication</summary>

- Set up separate Register and Login routes using react-router.
- Each of these routes should contain a form with the user's email, and password (and username, for the register form).
- The forms should submit post requests to their respective register/login routes on your server. You may need to do some research to figure out how to make the Fetch API send cookies in cross-origin requests.
- Send the user's credentials with any AJAX calls that require authentication on your server.
</details>
