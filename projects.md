# JS DOM releted projects

## project link
[click here](https://stackblitz.com/edit/dom-project-chaiaurcode-dctyngzt?file=1-colorChanger%2Findex.html)

# Solution Code

### project 1 --> Color Changer
```
const buttons = document.querySelectorAll('.button');
const body = document.querySelector('body');

buttons.forEach((button) => {
  // console.log(button);
  button.addEventListener('click', (e) => {
    console.log(e);
    console.log(e.target);
    // if(e.target.id === "grey"){
    //   body.style.backgroundColor = e.target.id
    // }
    // else if(e.target.id === "white"){
    //   body.style.backgroundColor = e.target.id
    // }
    // else if(e.target.id === "blue"){
    //   body.style.backgroundColor = e.target.id
    // }
    // else if(e.target.id === "yellow"){
    //   body.style.backgroundColor = e.target.id
    // }

    // using SwitchCase
    let color = e.target.id;
    switch (color) {
      case 'grey':
        body.style.backgroundColor = color;
        break;
      case 'white':
        body.style.backgroundColor = color;
        break;
      case 'blue':
        body.style.backgroundColor = color;
        break;
      case 'yellow':
        body.style.backgroundColor = color;
        break;
      default:
        console.log('You Clicked at wrong place!!');
        break;
    }
  });
});

```

### project 2 --> BMI Generator

```
const form = document.querySelector('form');
console.log(form);

form.addEventListener('submit', (e) => {
  <!-- for preventing submitting data to the server -->
  e.preventDefault();

  const height = parseInt(document.querySelector('#height').value);
  const weight = parseInt(document.querySelector('#weight').value);
  const results = document.querySelector('#results')
if(height === '' || height < 0 || isNaN(height)){
  results.textContent = `please give a valid height ${height}`
}else if(weight === '' || weight < 0 || isNaN(weight)){
  results.textContent = `please give a valid weight ${weight}`
}else{
  const bmi = (weight / ((height * height)/10000)).toFixed(2)
  if(bmi < 18.6){
    results.innerHTML = `<span>${bmi} --> Under Wight </span>`
  }else if (bmi > 18.6 && bmi < 24.9){
    results.innerHTML = `<span>${bmi} --> Normal Wight </span>`
  }
  else{
    results.innerHTML = `<span>${bmi} --> Greater Wight </span>`
  }
}

});


```

### project 3 --> Digital Clock

```
 <!-- const clock = document.querySelector('#clock') -->
const clock = document.getElementById('clock')
console.log(clock)


setInterval( ()=>{
  let date = new Date()
  // console.log(date.toLocaleTimeString())
  clock.innerHTML = date.toLocaleTimeString()
  
},1000)


```
### project 4 --> Guess The Number

```
let randomNumber = parseInt(Math.random() * 100 + 1);
// console.log(randomNumber);
let userInput = document.querySelector('#guessField');
// console.log(userInput);
let submit = document.querySelector('#subt');
let guessSlot = document.querySelector('.guesses');
let remaining = document.querySelector('.lastResult');
let lowOrHi = document.querySelector('.lowOrHi');
let satrtOver = document.querySelector('.resultParas');

const p = document.createElement('p');

let preGuess = [];
let numGuess = 1;

let playGame = true;

if (playGame) {
  submit.addEventListener('click', (e) => {
    e.preventDefault();
    const guess = parseInt(userInput.value);
    // console.log(guess)
    validateGuess(guess);
  });
}

function validateGuess(guess) {
  if (isNaN(guess)) {
    alert(`Please Enter a Valid Number`);
  } else if (guess > 100) {
    alert(`Please entered less than 100 Your number is ${guess}`);
  } else if (guess < 1) {
    alert(`Please entered greater than 0 Your number is ${guess}`);
  } else {
    preGuess.push(guess);
    displayGuess(guess);
    if (numGuess === 11) {
      displyMessage(`Game Over, Random number is ${randomNumber}`);
      endGame();
    } else {
      checkGuess(guess);
    }
  }
}

function checkGuess(guess) {
  if (guess === randomNumber) {
    displyMessage(`You guessed it right!!`);
    endGame();
  } else if (guess > randomNumber) {
    displyMessage(`You guessed it TOO high`);
  } else {
    displyMessage(`You guessed it TOO low`);
  }
}

function displayGuess(guess) {
  userInput.value = '';
  guessSlot.innerHTML += `${guess} `;
  numGuess++;
  remaining.innerHTML = `${11 - numGuess}`;
}

function displyMessage(message) {
  lowOrHi.innerHTML = `<h2>${message}</h2>`;
}

function endGame() {
  userInput.value = '';
  userInput.setAttribute('disabled', '');
  p.classList.add('button');
  p.innerHTML = `<h2 id='newGame'>Start a new Game</h2>`;
  satrtOver.appendChild(p);
  playGame = false;
  newGame();
}

function newGame() {
  const newGameButton = document.querySelector('#newGame');
  newGameButton.addEventListener('click', () => {
    randomNumber = parseInt(Math.random() * 100 + 1);
    preGuess = [];
    numGuess = 1;
    guessSlot.innerHTML = '';
    remaining.innerHTML = `${11 - numGuess}`;
    userInput.removeAttribute('disable');
    satrtOver.removeAttribute('p');
    playGame = true;
  });
}


```