# Pre-work - *Memory Game*

**Memory Game** is a Light & Sound Memory game to apply for CodePath's SITE Program. 

Submitted by: **Karina Zhang**

Time spent: **8** hours spent in total

Link to project: https://glitch.com/edit/#!/peppered-sleepy-purchase

## Required Functionality

The following **required** functionality is complete:

* [x] Game interface has a heading (h1 tag), a line of body text (p tag), and four buttons that match the demo app
* [x] "Start" button toggles between "Start" and "Stop" when clicked. 
* [x] Game buttons each light up and play a sound when clicked. 
* [x] Computer plays back sequence of clues including sound and visual cue for each button
* [x] Play progresses to the next turn (the user gets the next step in the pattern) after a correct guess. 
* [x] User wins the game after guessing a complete pattern
* [x] User loses the game after an incorrect guess

The following **optional** features are implemented:

* [x] Any HTML page elements (including game buttons) has been styled differently than in the tutorial
* [x] Buttons use a pitch (frequency) other than the ones in the tutorial
* [x] More than 4 functional game buttons
* [x] Playback speeds up on each turn
* [x] Computer picks a different pattern each time the game is played
* [x] Player only loses after 3 mistakes (instead of on the first mistake)
* [ ] Game button appearance change goes beyond color (e.g. add an image)
* [ ] Game button sound is more complex than a single tone (e.g. an audio file, a chord, a sequence of multiple tones)
* [ ] User has a limited amount of time to enter their guess on each turn

The following **additional** features are implemented:

- [x] Responsive for different screen sizes (mobile, tablet, desktop)

## Video Walkthrough

Here's a walkthrough of implemented user stories:
![walkthrough](https://user-images.githubusercontent.com/41274792/112898927-79149280-90af-11eb-99cc-5dbe07f94643.gif)

## Reflection Questions
1. If you used any outside resources to help complete your submission (websites, books, people, etc) list them here. 

   I consulted the website w3 schools for css syntax and for animating the start and stop buttons.
   
2. What was a challenge you encountered in creating this submission (be specific)? How did you overcome it? (recommended 200 - 400 words) 

   When I finished the main part of the project, I decided to add additional game buttons to increase the difficulty. I created nine buttons, but much of the work was repeated so I wanted to iteratively create the buttons. To make this a bit easier, I created a div with an id of “gameButtonArea” in which I could add each button using the following:
   ```JavaScript
   let gameButtonArea = document.getElementById("gameButtonArea");
   for (let i = 1; i < 10; i++) {
        gameButtonArea.innerHTML += `<button id="button${i}" onclick="guess(${i})" onmousedown="startTone(${i})" onmouseup="stopTone()"></button>`;
   }
   ```
   This worked great so I wanted to take it a step further and set the CSS styles in the same way. I created arrays of the buttons’ default and active colors, but when I went to set them, I found that the active state of a button cannot be set using javascript as it is a CSS-specific pseudoclass. In exploring alternatives, I tested using event listeners that listened for “onclick” and “onfocus”  While “onfocus” was mildly successful, resulting in the buttons lighting up, it did not return the button to its default color after clicking. I resigned myself to writing out the individual CSS styles for each active state, but wanted to at least set the default button colors using JavaScript. I used the following code:
   ```JavaScript
   let currentButton = document.getElementById(`button${i}`);
   currentButton.style.backgroundColor = colorsArray[i-1];
   ```
   This was successful in setting the default button colors, but now the active state colors did not show up when I clicked buttons or when a sequence was playing. At this point, I wanted to focus my attention on implementing new functionalities into the project rather than optimizing this one area. I set the individual CSS styles for the buttons and used the time I saved to implement optional features such as increasing the speed the sequence is played at over time, using a random pattern, giving the player 3 strikes, and cleaning up the UI to make it responsive for screens of all different sizes.

3. What questions about web development do you have after completing your submission? (recommended 100 - 300 words) 

   Through my struggles with setting CSS styles using JavaScript, I learned there are many different ways to accomplish the same result (or in my case, attempt to accomplish). One question I am left with after completing my submission is what are some of the best practices of web development. This project is also a very visual application and I am curious about how one goes about developing web pages to be more accessible. Finally, I am still searching for a solution to iteratively setting my buttons’ active state CSS. I am currently looking into CSS preprocessors such as SASS and LESS as potential solutions, but I still wonder how feasible it is to use JavaScript to accomplish this.

4. If you had a few more hours to work on this project, what would you spend them doing (for example: refactoring certain functions, adding additional features, etc). Be specific. (recommended 100 - 300 words) 

   I noticed while testing my project that sometimes, the user will forget how many tones are supposed to play during the round and start clicking buttons early. Something I would want to implement if  I had the extra time would be a visual indicator to mark the period during which the user can make their guesses. I would also make it impossible to start clicking game buttons before the sequence has finished playing. Otherwise, users may start inputting their guesses, stop when they see that there was more to the sequence, and then restart their guesses, which immediately results in a wrong guess and discourages the player.
I also started implementing the time limit for players’ guesses, only finishing up to the UI of the timer. Next steps would include connecting this to start counting down when the sequence is done playing, resetting when the user correctly clicks the last button in that given sequence or clicks the wrong button, and displaying a message when the user runs out of time and decrementing the number of guesses left.

## License

    Copyright Karina Zhang

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
