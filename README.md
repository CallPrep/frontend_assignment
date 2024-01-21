# Frontend Assignment

Below mentioned is a **Random JSON Generator** in javascript, which generates a random json.

```jsx
function generateRandomJSON() {
  
  // Generate a random string of fixed length
  function randomString(length = 5) {
    const letters = 'abcdefghijklmnopqrstuvwxyz';
    let result = '';
    for (let i = 0; i < length; i++) {
      result += letters.charAt(Math.floor(Math.random() * letters.length));
    }
    return result;
  }
  
  // Generate a random number up to max_value
  function randomNumber(maxValue = 100) {
    return Math.floor(Math.random() * maxValue) + 1;
  }
  
  // Recursive function to create an element with a minimum depth and width
  function createElement(depth) {
    if (depth === 0) {
      // Base case: return a random string or number
      return Math.random() < 0.5 ? randomString() : randomNumber();
    } else {
      // Decides to create a dictionary with random key-value pairs
      const dictLength = Math.max(Math.floor(Math.random() * width), 2); // Ensure minimum width of 2
      const obj = {};
      for (let i = 0; i < dictLength; i++) {
        obj[randomString()] = createElement(depth - 1);
      }
      return obj;
    }
  }
  
  // Generate random depth and width for the data structure with a minimum depth of 2
  const depth = Math.max(Math.floor(Math.random() * 10), 2); // Ensure minimum depth of 2
  const width = Math.max(Math.floor(Math.random() * 4), 2); // Ensure minimum width of 2

  // Create a top-level array containing dictionaries
  const listLength = Math.max(Math.floor(Math.random() * width), 2); // Ensure a minimum length of 2 for the outer list
  const randomData = Array.from({ length: listLength }, () => createElement(depth - 1)); // -1 because the outer list adds a level of depth

  // Convert the data to a JSON string
  return JSON.stringify(randomData, null, 2);
}

// Test the function
console.log(generateRandomJSON());
```

## Task 1: Create the Frontend to Display JSON and Provide a Generation Button

You need to create a simple front-end application, possibly using a framework such as React, Vue, or Angular. It should include the following:

1. A view area where the generated JSON is displayed.
2. A button that triggers the `generateRandomJSON` function to create a new JSON and display it in the view area.

## Task 2: Create a Card Component for Displaying JSON

Create a component that displays each JSON dictionary on its own card. These cards should clearly show the structure of the JSON, with sub-objects and arrays formatted to indicate their nesting levels. Use visual elements like indents or tags to help show the relationships between different parts of the JSON data.

**Remember, the JSON generator produces a list of dictionary objects, and you need to make a separate card for each dictionary in the list.**

### Guidelines for Implementation:

1. Construct a `Card` component that formats and styles the JSON content.
2. Use visual indentation, like tree views, to represent nested objects and arrays.
3. Keep the design clean and minimalistic, ensuring readability of the JSON content.
4. Optionally, use collapsible sections for deeply nested structures to avoid overwhelming users with too much information at once.

## Additional Tasks

- Implement error handling for cases where the JSON generation could fail.
- Style the cards to be visually appealing and ensure that the layout is responsive for different screen sizes.
- Add functionality to copy the JSON to the clipboard.
- Allow users to download the generated JSON as a `.json` file.
- Create a search feature that filters the visible JSON cards based on user input.

## Bonus Task: Generative AI for Contextual Icons

Leverage AI, such as OpenAI's DALL·E or GPT4 Vision API, to generate icons that match the context of each card. Alternatively, if there's no access to GPT4, use Heroicons library and GPT3.5 (or other OpenAI's text API) to programmatically select icons based on the card's content or key names.

## Task 3: Host on Firebase

Finally, deploy and host your application on Firebase, which offers hosting services. You'll need to:

1. Build your project for production.
2. Initialize a Firebase project using Firebase CLI.
3. Deploy your built application using Firebase Hosting features.

### Steps for Firebase Hosting:

- Install Firebase CLI and login to your account.
- Initiate your project with `firebase init` and select hosting.
- Build your application (`npm run build`).
- Deploy using `firebase deploy`.

In case of any queries related to the assignment, please reach out at [bhavesh@callprep.io](mailto:bhavesh@callprep.io)
