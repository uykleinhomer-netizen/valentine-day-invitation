<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Valentine's Invitation</title>
<style>
  body {
    font-family: 'Comic Sans MS', cursive, sans-serif;
    background: linear-gradient(to right, #ff9a9e, #fad0c4);
    margin: 0;
    overflow: hidden;
    text-align: center;
    color: #fff;
  }

  h1 {
    font-size: 3em;
    margin-top: 40px;
    text-shadow: 2px 2px #e75480;
  }

  #countdown {
    font-size: 1.5em;
    margin: 10px 0 30px 0;
  }

  button {
    background-color: #e75480;
    border: none;
    padding: 15px 30px;
    font-size: 1.2em;
    border-radius: 10px;
    color: white;
    cursor: pointer;
    box-shadow: 2px 2px 10px rgba(0,0,0,0.2);
    transition: transform 0.2s;
    margin-bottom: 20px;
  }

  button:hover {
    transform: scale(1.1);
    background-color: #ff5c8d;
  }

  #surprise {
    display: none;
    font-size: 2em;
    margin-bottom: 40px;
  }

  .heart {
    color: #ff1a75;
    animation: heartbeat 1s infinite;
  }

  @keyframes heartbeat {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.2); }
  }

  .flying-heart {
    position: absolute;
    font-size: 2em;
    animation: floatUp linear infinite;
    pointer-events: none;
  }

  @keyframes floatUp {
    0% { transform: translateY(100vh) scale(1); opacity: 1; }
    100% { transform: translateY(-10vh) scale(0.5); opacity: 0; }
  }
</style>
</head>
<body>

<h1>💖 My Love 💖</h1>
<div id="countdown"></div>
<button onclick="revealSurprise()">Click to see your invitation ❤️</button>
<div id="surprise">
  <p class="heart">🌹 Be my Valentine! 🌹</p>
  <p>Let's celebrate together this Valentine's Day ❤️</p>
</div>

<audio id="bgMusic" autoplay loop>
  <source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3" type="audio/mpeg">
</audio>

<script>
  // Reveal surprise
  function revealSurprise() {
    document.getElementById('surprise').style.display = 'block';
  }

  // Countdown Timer
  const countdownEl = document.getElementById('countdown');
  const valentineDate = new Date("Feb 14, 2026 00:00:00").getTime();

  function updateCountdown() {
    const now = new Date().getTime();
    const distance = valentineDate - now;

    const days = Math.floor(distance / (1000 * 60 * 60 * 24));
    const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000*60*60));
    const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000*60));
    const seconds = Math.floor((distance % (1000 * 60)) / 1000);

    countdownEl.innerHTML = `Valentine's Day is in ${days}d ${hours}h ${minutes}m ${seconds}s`;

    if(distance < 0){
      countdownEl.innerHTML = "Happy Valentine's Day! 💕";
    }
  }
  setInterval(updateCountdown, 1000);

  // Flying hearts
  function createHeart(){
    const heart = document.createElement('div');
    heart.className = 'flying-heart';
    heart.innerHTML = '💖';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = 5 + Math.random() * 5 + 's';
    document.body.appendChild(heart);

    setTimeout(() => {
      heart.remove();
    }, 10000);
  }
  setInterval(createHeart, 500);
</script>

</body>
</html>
