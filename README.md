# WordSearchGame-SpringBoot-Vanilla-JS-HTML-SASS-Parcel-Babel

# Demonstration :-
Word-Search game UI

![word search game UI](https://github.com/Lucifer7355/WordSearchGame-SpringBoot-Vanilla-JS-HTML-SASS-Parcel-Babel/blob/main/demonstration_picture/Screenshot%20(268).png)

A backend REST-API call is made after clicking on generate grid and response obtained is parsed as grid in UI.

![A backend REST-API call is made after clicking on generate grid and response obtained is parsed as grid in UI.](https://github.com/Lucifer7355/WordSearchGame-SpringBoot-Vanilla-JS-HTML-SASS-Parcel-Babel/blob/main/demonstration_picture/Screenshot%20(270).png)

![A backend REST-API call is made after clicking on generate grid and response obtained is parsed as grid in UI.](https://github.com/Lucifer7355/WordSearchGame-SpringBoot-Vanilla-JS-HTML-SASS-Parcel-Babel/blob/main/demonstration_picture/Screenshot%20(269).png)
# Wordgrid Backend-Service(SpringBoot):
 
Given Some words and grid size, We have to generate a boggle grid and return to front end after serializing the result as String.
Methodology:
1. There are 8 possible directions namely :-  HORIZONTAL,VERTICAL,DIAGONAL,HORIZONTAL_INVERSE,VERTICAL_INVERSE,DIAGONAL_INVERSE.
2. If x is number of rows and y is number of columns in grid, then number of possible coordinates to consider in the grid is x*y;
3. In the Grid creation service I have considered 8 Directions as enum and Coordinate class to keep track of coordinates as objects.
4. generateGrid function takes input of gridsize to be generated (which is always a square matrix in case of boggle game).
   Following steps are done inside this function:-
   * created a list of coordinates and 2-D matrix of size given in the input.
   * added each of the available coordinates inside the list and initialized matrix with '_'.
   * now started to iterate for each word and in each iteration Coordinates are selected from Coordinates list after shuffling the list.
   * After that we have to select the direction for current word to put into. This is decided by calling getDirectionForFit function.
   * Inside the getDirectionForFit function it considers all 8 directions and checks if the current word can be placed as a whole in a particular direction by calling doesFit function.
   * doesFit function returns true if word can be placed as a whole in a particular direction else it returns false.
   * if current word cannot be placed in any of the 8 directions, getDirectionForFit return null.
   * Now inside the generateGrid Function It will get the required direction in which a word can be placed and according to that the word is placed inside the matrix.
   * This Iteration continues till all the mentioned words from the list are completely listed inside the matrix.
   * After that randomFillGrid function is called which takes the grid and fills the leftover positions which are present as '_' after filling the given words to one of the block alphabetical letters to hide the given words randomly inside the grid.
   * after that the service returns the required 2-D grid from function.
5. The controller function gets the grid, Serializes it and sends it to the client where is can be deserialized and processed as per need.

# Wordgrid FrontEnd-Service(HTML+SASS+VANILLA JS + PARCEL + BABEL):

On The Front-End Side We have used vanilla javascript,HTML,and SCSS to style our UI and make cross-origin API calls.
1. .babelrc is mandatory to create for browser to understand modern javascript paradigms.
2. parcel is used to bundle and server the whole UI content(static) on http://localhost:1234.
3. On The UI side made REST API call to get Grid data using javascript and created logic for mouseup,mousedown and mousemove. Due to this the required words which we have to seach in the game 
   will be highlighted when we find them and do mousedown--->mousemove--->mouseup.
4. Hence this is the simple game logic implemented in UI.
5. The bundled files can be put in the backend of SpringBoot to make Single place hosting of both Backend and FrontEnd.

# Installation Steps:-

```
steps to start front-end:
- npm i
- npm install babel
- npm install sass
- npx parcel src/index.html

steps to start back-end:
- Just simply start the springboot server and http://localhost:1234 is already whitelisted in the backend. It can whitelist any other url as per requirements.
```
```
steps to start back-end:
- Just simply start the springboot server and http://localhost:1234 is already whitelisted in the backend. It can whitelist any other url as per requirements.
```

### Now Request grid--->Receive Response---> Play Boggle word search game.

---

# Extras:-

To learn more about parcel.

https://www.digitalocean.com/community/tutorials/how-to-bundle-a-web-app-with-parcel-js

