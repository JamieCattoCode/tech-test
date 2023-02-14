# Technical Test: NASA Image Search

The brief of the test was to build a React-based web application that allows users to search for images based on a query relating to space.
I was provided the NASA API endpoints for the image search.
The app needed to have the following functionalities:
- A search page which allows users to search for images by keyword
- Images must be returned upon a successful search

## Screenshots of the app working
When the user opens the app they're shown this screen:
![Opening screen](/public/screenshot-empty-search.png)

If they type in a successful search term they will see something like this:
![Moon search results](/public/screenshot-moon-search.png)

If they type in an unsuccessful search term they will see this:
![Unsuccessful search](/public/screenshot-unsuccessful.png)

## What was the app built with?
This app was built with Create React App, initially using the `npx create-react-app` command.

Therefore, React components are responsible for the bulk of the app's functionality.

## Testing utilities used
For this app I used a combination of Jest and React Testing library.
Here is a sample of the code testing the SearchResults React component:
```
import React from "react";
import { render, screen } from "@testing-library/react";
import SearchResults from "../components/SearchResults";

describe("SearchResults", () => {
  const validProps = [
    'image 1',
    'image 2'
  ];

  const { asFragment } = render(<SearchResults results={validProps}/>);


  it("renders correctly", () => {
    expect(asFragment()).toMatchSnapshot();
  });

  it('renders only text if there are no results', () => {
    const invalidProps = [];

    render(<SearchResults results={invalidProps} />);

    expect(screen.getByText('No results.')).toBeInTheDocument();
  });
```

## Packages used
### Axios
Axios is a Promise-based HTTP client for Node.js and the browser.
This allowed me to get json data from the NASA API endpoints and use it in my code.
You can install axios using `npm install axios`.
I imported it into the necessary files using `import axios from 'axios';`

### PropTypes
PropTypes is React's internal mechanism for dealing with the validation of props between components.
I used it so that it would be easier to spot when incorrect props were being passed between components, so as to make the debugging process much simpler.
The package is installed using `npm install prop-types -save` and imported into a React component with `import PropTypes from 'prop-types';`

## How to run the app
### (1) Clone the repository
The first step to running the app is cloning this repository with `git clone https://github.com/JamieCattoCode/tech-test.git`.
### (2) Install dependencies
We install the app's dependencies locally using `npm install`
### (3) Run the app locally
To run the app on your localhost, type the `npm start` command in the repository root.
### (4) Use the app
Using the app yourself is very simple - simply type in your desired search term into the search box and hit `ENTER` or press the 'Search' button.
### (5) Test the app
You can return to your repository to test the app with the `npm test` command.

## Things I would do if I had more time
If I had more time to work on the app, I would:
- Improve the styling for a better and smoother user experience
- Give some context to the images (e.g. a caption) when hovering over them
- Improve the responsiveness so that the app can be used across different devices

## Author
### Jamie Catto
[LinkedIn](https://www.linkedin.com/in/jamie-catto-6876421b8/)

[Twitter](https://twitter.com/CodesJmt)

[GitHub](https://github.com/JamieCattoCode)