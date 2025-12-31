<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Happy Birthday Nistha 🎉</title>

<style>
body {
  margin: 0;
  height: 100vh;
  overflow: hidden;
  background: linear-gradient(135deg, #fbc2eb, #a6c1ee);
  font-family: 'Segoe UI', sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
}

.card {
  background: white;
  padding: 35px;
  border-radius: 25px;
  max-width: 520px;
  text-align: center;
  box-shadow: 0 15px 30px rgba(0,0,0,0.2);
  animation: popIn 1.2s ease;
  z-index: 2;
}

@keyframes popIn {
  0% { transform: scale(0.5); opacity: 0; }
  100% { transform: scale(1); opacity: 1; }
}

h1 {
  color: #c9184a;
  font-size: 2.7em;
  animation: glow 2s infinite alternate;
}

@keyframes glow {
  from { text-shadow: 0 0 5px #ffafcc; }
  to { text-shadow: 0 0 15px #ff4d6d; }
}

.name {
  font-size: 1.6em;
  color: #6a0572;
  font-weight: bold;
}

p {
  font-size: 1.15em;
  margin: 12px 0;
}

button {
  margin-top: 15px;
  padding: 12px 22px;
  border: none;
  border-radius: 20px;
  background: #ff4d6d;
  color: white;
  font-size: 1em;
  cursor: pointer;
  transition: transform 0.2s;
}

button:hover {
  transform: scale(1.1);
}

.surprise {
  display: none;
  margin-top: 15px;
  font-size: 1.25em;
  color: #720026;
  animation: fadeIn 1s ease;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Floating hearts */
.heart {
  position: absolute;
  font-size: 20px;
  animation: floatUp 3s linear forwards;
}

@keyframes floatUp {
  to {
    transform: translateY(-100vh);
    opacity: 0;
  }
}

/* Confetti */
.confetti {
  position: absolute;
  width: 10px;
  height: 10px;
  top: -10px;
  animation: fall linear infinite;
}

@keyframes fall {
  to {
    transform: translateY(110vh) rotate(360deg);
  }
}

img {
  display: none;
  margin-top: 15px;
  width: 200px;
  border-radius: 15px;
  animation: fadeIn 1s ease;
}
</style>
</head>

<body>

<div class="card">
  <h1>🎉 Happy Birthday 🎉</h1>
  <div class="name">Nistha Jain</div>

  <p>
    Wishing you a day filled with smiles, happiness,  
    and lots of positive moments ✨
  </p>

  <p>
    May this year bring success, peace,  
    and beautiful memories 🌸
  </p>

  <button onclick="showSurprise()">Click for a surprise 🎁</button>

  <div class="surprise" id="msg">
    🎉 You are a wonderful person — stay happy and keep shining 💖
  </div>

  <img src="photo.jpg" id="photo" alt="Birthday memory">

  <audio controls autoplay>
    <source src="birthday.mp3" type="audio/mpeg">
  </audio>
</div>

<script>
// Confetti
function confetti(count) {
  for (let i = 0; i < count; i++) {
    let c = document.createElement("div");
    c.className = "confetti";
    document.body.appendChild(c);

    c.style.left = Math.random() * 100 + "vw";
    c.style.backgroundColor =
      ["#ff4d6d", "#ffd166", "#06d6a0", "#4d96ff", "#cdb4db"]
      [Math.floor(Math.random() * 5)];

    c.style.animationDuration = (Math.random() * 3 + 2) + "s";
  }
}
confetti(60);

// Floating hearts
function hearts() {
  for (let i = 0; i < 15; i++) {
    let h = document.createElement("div");
    h.className = "heart";
    h.innerHTML = "❤️";
    document.body.appendChild(h);

    h.style.left = Math.random() * 100 + "vw";
    h.style.top = "90vh";
    setTimeout(() => h.remove(), 3000);
  }
}

function showSurprise() {
  document.getElementById("msg").style.display = "block";
  document.getElementById("photo").style.display = "block";
  confetti(40);
  hearts();
}
</script>

</body>
</html>

