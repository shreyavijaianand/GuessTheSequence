// Start on the Home Screen
setScreen("HomeScreen");

// Handle Return to Home button click
onEvent("ReturntoHomeScreen", "click", function() {
  // Reset variables
  guessedSequence = [];
  sequence = [];
  generateSequence(sequenceLength);
  
  // Reset screen and messages
  setScreen("HomeScreen");
  setText("MessagesTitle", "Select a Number");
  setText("ConfirmationLabel", "Sequence: ");
  setText("QuestionTitles", "Guess the next number in the sequence");
});

// Handle Play button click
onEvent("PlayButton", "click", function() {
  setScreen("QuestionScreen");
});

// Handle Directions button click
onEvent("DirectionButton", "click", function() {
  setScreen("DirectionScreen");
});

// Handle return from Directions to Play
onEvent("DirectiontoPlayButton", "click", function() {
  setScreen("QuestionScreen");
});

// Define the sequence and guessed sequence arrays
var sequence = [];
var guessedSequence = [];

// Function to generate a random sequence
function generateSequence(length) {
  sequence = [];
  for (var i = 0; i < length; i++) {
    appendItem(sequence, Math.floor(Math.random() * 4 + 1)); // Generates random numbers between 1 and 4
  }
}

// Function to check if a guess is correct
function checkGuess(guess) {
  var nextNumber = sequence[guessedSequence.length]; // Get the next number in the sequence
  return guess === nextNumber;
}

var sequenceLength = 4; // Length of the sequence

// Generate the initial sequence
generateSequence(sequenceLength);

// Display the initial message
setText("MessagesTitle", "Select a Number");
setText("ConfirmationLabel", "Sequence: ");
setText("QuestionTitles", "Guess the next number in the sequence");

// Button event listeners for guessing numbers
onEvent("OneButton", "click", function() {
  checkAndProvideFeedback(1);
});

onEvent("TwoButton", "click", function() {
  checkAndProvideFeedback(2);
});

onEvent("ThreeButton", "click", function() {
  checkAndProvideFeedback(3);
});

onEvent("FourButton", "click", function() {
  checkAndProvideFeedback(4);
});

// Function to check guess and provide user feedback
function checkAndProvideFeedback(guess) {
  // Check the guess
  if (checkGuess(guess)) {
    setText("MessagesTitle", "Congratulations! You guessed correctly.");
    appendItem(guessedSequence, guess);
    setText("ConfirmationLabel", "Sequence: " + guessedSequence.join(", ")); // Update the displayed sequence

    // Check if more guesses are needed
    if (guessedSequence.length < sequenceLength) {
      setText("QuestionTitles", "Guess the next number in the sequence");
    } else {
      setText("MessagesTitle", "Congratulations! You guessed the whole sequence.");
      setText("QuestionTitles", "Click the Home Screen Button to Play Again!");
    }
  } else {
    // Incorrect guess
    setText("MessagesTitle", "Sorry, that's incorrect. Try again!");
  }
}
