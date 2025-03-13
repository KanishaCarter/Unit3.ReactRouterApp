Overview
What We Are Building
Our goal in the workshop is to build a simple application that navigates between two routes /blue and /red. Each will render a simple component with the background being that specific color. It will be something like this:

View of workshop, a header with three links, blue, red and home, with a page with the respective color displayed behind it

We will utilize the components from React Router to build out our functionality. There are no hooks for this workshop.

Initialize the Project
By now, you should be comfortable spinning up a React application with Vite. As a reminder, run npm create vite@latest, follow all prompts to name your project, then select React and JavaScript as well.

If you need, reference the Vite documentation or past workshops.

Follow the instructions in the terminal to navigate into the directory npm install and open your project in vscode.

Finally, remove the boilerplate JSX, leaving only an empty react fragment in your App.jsx. We are ready now to start building. Use the npm run dev command and open the application in your browser.

1. Replace all of the index.css code with the following CSS:

index.css
 *{ font-family: arial, sans-serif;
  margin: 0;
}
body,
body > div {
  height: 100vh;
  width: 100vw;
}
#container {
  height: 100%;
  display: flex;
  flex-direction: column;
}
#container > div {
  display: flex;
}
#navbar {
  padding: 2em;
  justify-content: space-evenly;
}
#main-section {
  flex-grow: 1;
}
#main-section > div {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.red {
  background-color: #b05f6d;
  color: white;
}
.blue {
  background-color: #275db3;
  color: white;
}
We will be referencing these CSS styles while we build out our application.

2. Next, in your App.jsx, replace the empty React Fragment with the following code:

Show Code
    <div id="container">
      <h1>Hello React Router!</h1>
      <div id="navbar">{/* navigation here */}</div>
      <div id="main-section">{/* routes here */}</div>
    </div>

React Router Configuration
1. Install the React Router package with npm install react-router-dom

2. Navigate to your main.jsx and import { BrowserRouter } from "react-router-dom";

3. You will observe the React Strict mode component surrounds our component. Inside the Strict mode component, wrap your App.jsx component with the Browser Router tag. This will give our entire application access to the React Router API.

Nesting
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
Navigate back to your App.jsx and let us inspect the code. Inside of our parent div, we have three children, A h1, and two other divs with IDs of "navbar" and "main-section". This "main section" is where we will be creating our Routes, and the "navbar" will be where we utilize the <Link> component to navigate between routes. At this point, let us remove our h1 message, as it will no longer be needed.

5. In this App.jsx import the Routes and Routes components from React Router import { Routes, Route } from "react-router-dom";

6. Remove the { } from within the "main-container" div and replace it with the Routes component.

Show Solution
<div id="main-section">
  <Routes>
     { // Individual Routes go here }    
  </Routes>
</div>
7. Next, we need to use the Route component and render two route components. One with the path property set to "/blue", the other "/red".

8. Add an element property to each Route tag and pass a simple h1 tag with a relevant heading for each component.

Main Container
<div id="main-section">
   <Routes>
     <Route path="/blue" element={<h1>Blue</h1>} />
     <Route path="/red" element={<h1>Red</h1>} />
   </Routes>
</div>

At this point, we actually already have our basic functionality implemented. In your browser window, add either /blue or /red to the URL bar and hit enter. You should observe our dummy h1 elements rendered when the URL route matches our defined routes.

Navbar and the Link component
If we wanted to modularize our code more, we could extract our navbar into a separate component, but for the sake of learning the basics, we will keep things simple and leave it in our App.jsx.

1. Add the Link component to the 'react-router-dom' import statement object.

Show Imports
import { Routes, Route, Link } from "react-router-dom";
2. In the div with the id of "navbar", remove the { } and create two Link tags. One should have a to property set to "/blue", and the other to "/red". Add some inner text to each Link set to "blue" and "red" respectively.

If you navigate back to your browser, you can observe a bare-bones navbar, with two links. Click on each link and notice both the components that are switching URLs are changing.

We now have some bare-bones routing set up. Let us now replace the dummy h1's passed to our Route components with actual components.

3. In your src directory, create a components folder and create two files, Red.jsx and Blue.jsx

4. In each file create a component which returns a div with the className set to its respective color. Inside of the div, create a h1 displaying the name of the color.

Red.jsx example
export default function Red() {
  return (
    <div className="red">
      <h1>RED</h1>
    </div>
  );
}
5. Navigate back to your App.jsx component and import your Blue and Red components into the file.

6. Now replace the "element" property for each route with the respective color component.

That is it! We have used all of the basic react-router components and made a simple yet smooth application that navigates between multiple components with React Router.

7. Next, notice what happens when you refresh the browser at your / route. You will observe that neither the Red nor the Blue component gets mounted. That is because there is no corresponding <Route> for our / URL. In your components folder, create a new file called Home.jsx. This is where we will make a landing page for our application.

8. In this home component, return a parent div element with a h1 saying "home".

9. Navigate back to your App.jsx import your Home component and create a new <Route> with the path of "/" which renders the Home component.

10. Add another Link component to our navbar, which navigates to the "/" route.

11. Lastly, in your Home component, add a className of home to the parent div, and in your index.css give your .home class a background color of your own choice.

Finishing Up
For the context of this small application, we will not be using the useParams or useNavigate hooks. However, in lessons to come, we will implement more complexity with our applications and utilize both hooks quite a bit.

As this workshop was relatively short, try and get some practice and implement the following stretch goals:

1. Break the navbar and main container up into separate components.

2. Create a few more <Routes> with new components.

3. Create a footer that sticks to the bottom of the page and has links to all of your <Routes>.

4. Give your app a general CSS facelift.

If you have finished all of the above, go ahead and run your build script with npm run build, and deploy your build folder to Netlify. You can also choose to deploy your application from a GitHub repository.

Criteria and Requirements:
1. The application is deployed without errors
2. The Application has a nav bar with at least three links, Red, Blue and Home
3. The application view changes upon a click to each link. The browser does NOT refresh, the url changes, and a view with the correct color shows up in the browser.
