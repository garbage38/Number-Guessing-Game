# PROJECTS ON DOM :

## PROJECT LINK 
[CLICK HERE TO SEE THE PROJECTS FILES](https://github.com/garbage38/Number-Guessing-Game)

# PROJECT NO. 4 Number Guessing Game
## SOLUTION :

```javascript
let number = parseInt(Math.random()*100 +1);

const submit = document.querySelector("#subt");
const userInput = document.querySelector("#guessField");
const guessSlot = document.querySelector(".guesses");
const remaining = document.querySelector(".lastResult");
const lowOrHi = document.querySelector(".lowOrHi");
const startOver = document.querySelector(".resultParas");

const p = document.createElement("p");

let prevGuess =[];
let numGuess=1;

let playGame =true;

if(playGame){
        submit.addEventListener("click",function(event){
           event.preventDefault();
        const guess =   parseInt(userInput.value);
        validateGuess(guess);
        })
}

function validateGuess(guess){
        // valid guess
        if(isNaN(guess)|| guess<1 || guess>100) {
            alert("enter valid number");
        }
        else{
                prevGuess.push(guess);
                if(numGuess>10){
                    displayMessage(guess);
                    displayMessage(`Game Over !! Random number was ${number}`);
                    endGame();
                }
                else{
                 displayGuess(guess);
                 checkGuess(guess);
                }
        }
        

}

function checkGuess(guess){
      if(guess === number){
        displayMessage(`You guessed it right at ${numGuess} th guess.`);
        endGame();
      }
      else if(guess < number){
        displayMessage(`Guess a Higer number`);
      }
      else{
        displayMessage(`Guess a lower number`);
      }
}

function displayGuess(guess){
   userInput.value ="";
   guessSlot.innerHTML += `${guess} `;
   numGuess++;
   remaining.innerHTML=`${11 - numGuess}`;

}

function displayMessage(message){
    //take message from user and display it
    lowOrHi.innerHTML = `<h2>${message}</h2>`;

}

function newGame(){
   const newGameBtn =  document.querySelector("#newGame");
   newGameBtn.addEventListener("click",function(event){
        number = parseInt(Math.random()*100 +1);
        prevGuess = [];
        numGuess =1;
        guessSlot.innerHTML = "";
        remaining.innerHTML =`${11 -numGuess} `;
        userInput.removeAttribute('disabled');
        startOver.removeChild(p);
        playGame = true;
   })
}

function endGame(){
   userInput.value = "";
   userInput.setAttribute('disabled','');
   p.classList.add('button');
   p.innerHTML=`<h2 id=newGame>Start new Game</h2>`;
   startOver.appendChild(p);
   playGame=false;
   newGame();
}
```
