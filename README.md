6
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>A Little Surprise ❤️</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  overflow: hidden;
  font-family: Arial, sans-serif;
  text-align: center;
  transition: background 0.8s ease;
}

.screen {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 25px;
}

.box {
  width: 100%;
  max-width: 420px;
}

h1 {
  color: white;
  font-size: 32px;
  margin-bottom: 25px;
}

p {
  color: white;
  font-size: 22px;
}

input {
  width: 90%;
  padding: 15px;
  border: none;
  border-radius: 30px;
  font-size: 18px;
  text-align: center;
  outline: none;
  margin: 15px 0;
}

button {
  border: none;
  border-radius: 30px;
  padding: 14px 28px;
  margin: 8px;
  font-size: 18px;
  font-weight: bold;
  cursor: pointer;
}

.yes {
  background: white;
  color: #1677ff;
}

.no {
  background: #222;
  color: white;
}

.continue {
  background: white;
  color: #ff4081;
}

/* STEP 1 */
.pink {
  background: linear-gradient(135deg, #ff4081, #ff79a7);
}

/* STEP 2 */
.blue {
  background: linear-gradient(135deg, #087cf5, #45c7ff);
}

/* STEP 3 */
.purple {
  background: linear-gradient(135deg, #6a11cb, #2575fc);
}

/* NO PHOTO */
#noScreen {
  background: #111;
  display: none;
}

#noScreen img {
  width: 90%;
  max-width: 500px;
  border-radius: 20px;
  box-shadow: 0 0 30px rgba(255,255,255,0.3);
}

/* LOVE SCREEN */
#loveScreen {
  display: none;
  background: radial-gradient(circle, #ff4d88, #8b0055);
  position: relative;
  overflow: hidden;
}

.loveText {
  position: absolute;
  color: white;
  font-size: 20px;
  font-weight: bold;
  pointer-events: none;
  animation: heartFloat 5s linear forwards;
  text-shadow: 0 0 10px white;
  white-space: nowrap;
}

@keyframes heartFloat {
  0% {
    opacity: 0;
    transform: scale(0.3);
  }

  15% {
    opacity: 1;
  }

  100% {
    opacity: 0;
    transform: scale(1.2);
  }
}

.bigLove {
  position: relative;
  z-index: 100;
  color: white;
  font-size: 38px;
  font-weight: bold;
  text-shadow: 0 0 20px white;
  animation: pulse 1s infinite;
}

@keyframes pulse {
  50% {
    transform: scale(1.12);
  }
}
</style>
</head>

<body>

<!-- STEP 1 -->
<div class="screen pink" id="step1">
  <div class="box">
    <h1>Hi 👋<br>My name is Avishek ❤️</h1>

    <p>And you?</p>

    <input
      type="text"
      id="name"
      placeholder="Type your name..."
    >

    <br>

    <button class="continue" onclick="goStep2()">
      Continue 💕
    </button>
  </div>
</div>


<!-- STEP 2 -->
<div class="screen blue" id="step2" style="display:none;">
  <div class="box">

    <h1>Can I ask you something? 👀</h1>

    <button class="yes" onclick="goStep3()">
      YES ❤️
    </button>

    <button class="no" onclick="showPhoto()">
      NO 😏
    </button>

  </div>
</div>


<!-- STEP 3 -->
<div class="screen purple" id="step3" style="display:none;">
  <div class="box">

    <h1>One little question 🤔</h1>

    <p>What is 266 − 123?</p>

    <input
      type="number"
      id="answer"
      placeholder="Your answer..."
    >

    <br>

    <button class="continue" onclick="checkAnswer()">
      Answer ❤️
    </button>

    <p id="wrong" style="display:none;">
      Hmm... try again 😜
    </p>

  </div>
</div>


<!-- NO SCREEN -->
<div class="screen" id="noScreen">
  <div class="box">

    

    <h1>😂 You chose NO!</h1>

  </div>
</div>


<!-- LOVE SCREEN -->
<div class="screen" id="loveScreen">

  <div class="bigLove" id="bigLove">
  </div>

</div>


<script>

let personName = "";


function goStep2() {

  let name = document.getElementById("name").value.trim();

  if (name === "") {
    alert("Please type your name ❤️");
    return;
  }

  personName = name;

  document.getElementById("step1").style.display = "none";
  document.getElementById("step2").style.display = "flex";

}


function goStep3() {

  document.getElementById("step2").style.display = "none";
  document.getElementById("step3").style.display = "flex";

}


function showPhoto() {

  document.getElementById("step2").style.display = "none";
  document.getElementById("noScreen").style.display = "flex";

}


function checkAnswer() {

  let answer = document.getElementById("answer").value;

  if (answer == "143") {

    startLove();

  } else {

    document.getElementById("wrong").style.display = "block";

  }

}


function startLove() {

  document.getElementById("step3").style.display = "none";
  document.getElementById("loveScreen").style.display = "flex";

  document.getElementById("bigLove").innerHTML =
    "I Love You, " + personName + " ❤️";

  createHeart();

}


function createHeart() {

  let count = 0;

  let timer = setInterval(function() {

    if (count >= 1000) {
      clearInterval(timer);
      return;
    }

    let love = document.createElement("div");

    love.className = "loveText";

    love.innerHTML =
      "I Love You, " + personName + " ❤️";

    /*
      Heart-shaped mathematical coordinates
    */

    let t = Math.random() * Math.PI * 2;

    let x =
      16 * Math.pow(Math.sin(t), 3);

    let y =
      -(13 * Math.cos(t)
      - 5 * Math.cos(2*t)
      - 2 * Math.cos(3*t)
      - Math.cos(4*t));

    let centerX = 50 + x * 2.5;
    let centerY = 50 + y * 2.5;

    love.style.left = centerX + "vw";
    love.style.top = centerY + "vh";

    love.style.animationDuration =
      (3 + Math.random() * 3) + "s";

    document.getElementById("loveScreen")
      .appendChild(love);

    setTimeout(function() {
      love.remove();
    }, 6000);

    count++;

  }, 35);

}

</script>

</body>
</html>
