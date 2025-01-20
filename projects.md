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
  //for preventing submitting data to the server
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