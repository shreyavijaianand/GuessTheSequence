# GuessTheSequence Description
This is a memory game where you guess a random sequence of numbers between 1 and 4. Guess each number in order—correct guesses are added to the sequence. If you're wrong, try again! Complete the sequence to win. You can view instructions or reset the game anytime from the Home Screen.

## Objective

- A random sequence of **4 numbers** (each from 1 to 4) is generated.
- The user must guess the sequence **in order**, one number at a time.
- Feedback is given for each guess:
  - Correct → progresses to the next number.
  - Incorrect → user is prompted to try again.
- Once the full sequence is guessed, the user wins and can play again.

---

## Screens Overview

| Screen ID         | Description                         |
|------------------|-------------------------------------|
| `HomeScreen`      | Main menu to start or view directions |
| `QuestionScreen`  | Game interface for making guesses    |
| `DirectionScreen` | Instructions on how to play          |

---

## Main Features

- Random sequence generation
- Guess tracking and validation
- Real-time feedback messages
- Replay functionality
- In-game directions

---

## Key Variables

```js
var sequence = [];         // The correct number sequence
var guessedSequence = [];  // User's correct guesses so far
var sequenceLength = 4;    // Sequence length (default is 4)
```

## Core Functions

### `generateSequence(length)`
Generates a random sequence of integers between 1 and 4 based on the specified length.

```javascript
function generateSequence(length) {
  sequence = [];
  for (var i = 0; i < length; i++) {
    appendItem(sequence, Math.floor(Math.random() * 4 + 1));
  }
}
```

### `checkGuess(guess)`
Checks whether the user's guess matches the next number in the generated sequence.

```javascript
function checkGuess(guess) {
  var nextNumber = sequence[guessedSequence.length];
  return guess === nextNumber;
}
```

### `checkAndProvideFeedback(guess)`
Handles user interaction after a guess. Updates the screen and text fields based on whether the guess was correct. If the full sequence is correctly guessed, it displays a success message.

```javascript
function checkAndProvideFeedback(guess) {
  if (checkGuess(guess)) {
    setText("MessagesTitle", "Congratulations! You guessed correctly.");
    appendItem(guessedSequence, guess);
    setText("ConfirmationLabel", "Sequence: " + guessedSequence.join(", "));

    if (guessedSequence.length < sequenceLength) {
      setText("QuestionTitles", "Guess the next number in the sequence");
    } else {
      setText("MessagesTitle", "Congratulations! You guessed the whole sequence.");
      setText("QuestionTitles", "Click the Home Screen Button to Play Again!");
    }
  } else {
    setText("MessagesTitle", "Sorry, that's incorrect. Try again!");
  }
}
```

---

## Button Event Handlers

The app listens for user interaction through several buttons. Each button triggers a different screen change or gameplay action.

| Button ID               | Action Triggered                                      |
|-------------------------|--------------------------------------------------------|
| `PlayButton`            | Switches to the question/game screen                   |
| `DirectionButton`       | Switches to the directions/instructions screen         |
| `DirectiontoPlayButton` | Returns from the directions screen to the game screen  |
| `ReturntoHomeScreen`    | Resets game variables and returns to the home screen   |
| `OneButton`             | Submits a guess of number `1`                          |
| `TwoButton`             | Submits a guess of number `2`                          |
| `ThreeButton`           | Submits a guess of number `3`                          |
| `FourButton`            | Submits a guess of number `4`                          |

---

## UI Text Fields Updated

These UI elements are dynamically updated based on user input and game state to provide real-time feedback.

| Element ID         | Description                                                |
|--------------------|------------------------------------------------------------|
| `MessagesTitle`    | Displays feedback on whether the user's guess was correct  |
| `ConfirmationLabel`| Shows the numbers guessed correctly so far                 |
| `QuestionTitles`   | Prompts the user to guess the next number or restart       |

---

## Tech Stack

This project uses the following tools and technologies:

- **Platform**: [Code.org App Lab](https://code.org/educate/applab)
- **Programming Language**: JavaScript
- **Development Environment**: Code.org's text-based IDE (App Lab)
- **Architecture**: Event-driven programming with dynamic screen management
- **User Interface**: Designed using Code.org's UI components
