## Pig Game - Game

_This project and README was made to enhance my personal learning._

This game was part of a Udemy course and the final solution is not entirely my own. I made small changes to challenge my self.

- The concept of this game is to have two users roll a dice and bank the number rolled on the dice as their score.
- After each roll, they player's score accumulates as long as they do not roll a 1.
- They can choose to continue rolling to increase their score or bank their score and start the other player's turn.
- The first player to reach a score of 100 wins the game.

#### Challenges

1. Implementing the rolling dice functionality
2. Displaying the dice roll
3. Check if the player rolled a 1
4. Add dice to the current score
5. Switch to next player
6. Holding functionality
7. Implementing a reset function

The game was pretty challenging for this stage of my learning but I learned a few neat tricks.

> Dynamically setting a file name to be chosen

```javascript
diceEl.src = `dice-${dice}.png`;
```

I find template literals really cool in general but using it this to dynamically chose file names based on logic can be really useful when designing front-end components.

> Creating the switchPlayer function

```javascript
const switchPlayer = function () {
  document.getElementById(`current--${activePlayer}`).textContent = 0;
  currentScore = 0;
  activePlayer = activePlayer === 0 ? 1 : 0;
  player0El.classList.toggle('player--active');
  palyer1El.classList.toggle('player--active');
};
```

> Creating the init() function to reset the game when the user clicks the new game button

```javascript
const init = function () {
  scores = [0, 0];
  currentScore = 0;
  activePlayer = 0;
  playing = true;

  score0El.textContent = 0;
  score1El.textContent = 0;
  current0El.textContent = 0;
  current1El.textContent = 0;

  diceEl.classList.add('hidden');
  player0El.classList.remove('player--winner');
  player1El.classList.remove('player--winner');
  player0El.classList.add('player--active');
  player1El.classList.remove('player--active');
};
```

This function takes all of the game variables and conditional styling and resets them back to their initial states. I first tried to create a reset function using the built in JavaScript reload method.

```javascript
btnNew.addEventListener('click', function () {
  location.reload();
});
```

While this worked for the purpose of just producing a new game state, the goal of the project was to have this feature reset the game within the browser without the users having to refresh the page. Thus the init() function was the better choice.
