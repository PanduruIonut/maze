# maze

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

General information
Max working time is three hours, after the time expires you must send the state of the code as a zip archive for all the php/html/js/css/sql code.
About the app
We have an UI that contains a form which collects and validates the following information:
* width and height;
* start coordinates;
* end coordinates;
* brick density, a percent of how many cells are bricks out of the total maze cells.

The data collected from the form will be used to create a maze.

The maze will have:
* width x height cells;
* an entry found at start coordinates;
* an exit found at end coordinates;
* randomly distributed bricks respecting the density provided in the UI;


If the maze has a solution, it means that there is a path containing no brick cells from entry to exit. Depending on the brick density and maze randomness, there may be cases where there are no solutions. In either case, the UI should do the following:
* moves the form to the side;
* displays the maze;
* animates the path if there is a solution;
* makes the non brick cells red if there is no path;
* the maze cells should scale to fit the inside a fixed size box at the right of the data collection form;

Other details
This is a progressive skill test. Think about what you are good at and prioritise, the goal is to show what you’re good at, we hope it’s everything, of course :) Focus on functionality but also on your coding style, we need to understand your thinking.

Here are some other details you should be aware of:
* you may use vanilla JS, jQuery, Vue.js or whatever you feel comfortable with to ease certain JavaScript implementation parts;
* do not use code found online for maze and path generation;
* feel free to implement any maze generation and solving algorithm with your own code you may use boilerplate only for grids/reset the app needs to work in Chrome, latest verion.
* feel free to tell us any other relevant details such as: how to setup your code, any special instructions, what you would have done better given you had more time and so on

UI - initial state

