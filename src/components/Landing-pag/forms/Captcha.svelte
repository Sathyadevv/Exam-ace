<script>
export let captchaCheck
import { createEventDispatcher , onMount} from 'svelte'
const dispatch = createEventDispatcher()
let captcha;
let reCaptcha;

let userInput;
let canvas;
let text = "";

const textGenerator = () => {
  let generatedText = "";
  // total 9 letters hence loop of 3
  for (let i = 0; i < 3; i++) {
    //65-90 numbers are capital letters
    generatedText += String.fromCharCode(randomNumber(65, 90));
    //97-122 are small letters
    generatedText += String.fromCharCode(randomNumber(97, 122));
    //48-57 are numbers from 0-9
    generatedText += String.fromCharCode(randomNumber(48, 57));
  }
  return generatedText;
};

const randomNumber = (min, max) =>
  Math.floor(Math.random() * (max - min + 1) + min);

//Canvas part
function drawStringOnCanvas(string) {
  let ctx = canvas.getContext("2d");
  ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height);
  const textColors = ["rgb(0,0,0)", "rgb(130,130,130)"];
  const letterSpace = 160 / string.length;
  for (let i = 0; i < string.length; i++) {
    const xInitialSpace = 12;
    ctx.font = "16px Roboto Mono";
    ctx.fillStyle = textColors[randomNumber(0, 1)];
    ctx.fillText(
      string[i],
      xInitialSpace + i * letterSpace,
      randomNumber(25, 40),
      100
    );
  }
}
const dispatchCaptcha = () =>{{
    captcha = {
        createdCaptcha:text,
        typedCaptcha:userInput
    }
} dispatch('captcha', captcha)};

const newCaptcha = () =>{{
    captcha = reCaptcha
} dispatch('newCaptcha', captcha)};

onMount(triggerFunction)


function triggerFunction() {
  userInput= "";
  text = textGenerator();
  console.log(text);
  //Randomize the text so that everytime the position of numbers and small letters is random
  text = [...text].sort(() => Math.random() - 0.5).join("");
  drawStringOnCanvas(text);
}

;

//call triggerFunction when page loads
// window.onload = () => triggerFunction();


</script>
<div class="containerr">
    <div class="wrapper">
      <canvas bind:this={canvas} id="canvas" width="200" height="44"></canvas>
      <button id="reload-button" on:click|preventDefault={()=>{triggerFunction();reCaptcha = false;newCaptcha()}}>
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-clockwise" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M8 3a5 5 0 1 0 4.546 2.914.5.5 0 0 1 .908-.417A6 6 0 1 1 8 2v1z"/>
            <path d="M8 4.466V.534a.25.25 0 0 1 .41-.192l2.36 1.966c.12.1.12.284 0 .384L8.41 4.658A.25.25 0 0 1 8 4.466z"/>
          </svg>
      </button>
    </div>
    <input
      type="text"
      id="user-input"
      placeholder="Enter the above text"
      bind:value={userInput} on:input={dispatchCaptcha}
    />
    <!-- <button id="submit-button" on:click|preventDefault={dispatchCaptcha}>Submit</button> -->
  </div>

  <style>
      * {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
/* body {
  height: 100vh;
  background: linear-gradient(135deg, #8052ec, #d161ff);
} */
.containerr {
    margin: 0;
    background-color: rgb(234, 235, 238);
  border-radius: 0.6em;
  /* position: absolute;
  transform: translate(-50%, -50%);
  top: 50%;
  left: 50%; */
  /* box-shadow: 0 1em 2em rgba(0, 0, 0, 0.25); */
}
.wrapper {
  display: flex;
  align-content: center;
  justify-content: space-between;
  gap: 1rem;
  margin: 1em 0;
}
canvas {
  border: 1px solid #000000;
  border-radius: 6px;
  background-color: #fff;
  width: 90%;
  border: rgb(207, 205, 205) 1px solid;
}
button#reload-button {
  font-size: 24px;
  width: 12%;
  background-color: #57b973;
  border: none;
  border-radius: 6px;
  color: #ffffff;
}
button#reload-button:hover {
    background-color: #2fa751;
}
input[type="text"] {
  font-family: "Roboto Mono", monospace;
  font-size: 1rem;
  padding: 3px;
  width: 100%;
  border: none;
  border-radius: 0.4em;
  border: rgb(207, 205, 205) 1px solid;

}
input[type="text"]:focus {
    outline: none;
}

  </style>