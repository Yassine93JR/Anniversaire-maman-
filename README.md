<!DOCTYPE html><html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🎁 Surprise Maman</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #0f0f0f;
      font-family: 'Segoe UI', sans-serif;
      overflow: hidden;
    }/* 🎁 Cadeau premium */
.gift {
  width: 140px;
  height: 140px;
  background: linear-gradient(135deg, #ff3c3c, #ff0000);
  position: relative;
  cursor: pointer;
  border-radius: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: bounce 1s infinite;
  box-shadow: 0 0 20px rgba(255,0,0,0.7);
}

.gift::before {
  content: '';
  position: absolute;
  width: 25px;
  height: 140px;
  background: gold;
}

.gift::after {
  content: '';
  position: absolute;
  width: 140px;
  height: 25px;
  background: gold;
}

@keyframes bounce {
  0%,100% { transform: translateY(0); }
  50% { transform: translateY(-12px) scale(1.05); }
}

/* 🎉 contenu */
.content {
  display: none;
  text-align: center;
  color: white;
  position: absolute;
  padding: 20px;
}

body.party {
  background: linear-gradient(-45deg, #ff9a9e, #fbc2eb, #a1c4fd, #fddb92);
  background-size: 400% 400%;
  animation: gradientBG 8s ease infinite;
}

@keyframes gradientBG {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

h1 {
  font-size: clamp(2em, 7vw, 3.5em);
  margin: 0;
  opacity: 0;
  animation: appear 2s forwards;
}

@keyframes appear {
  to { opacity: 1; transform: translateY(-10px); }
}

.date, .from {
  opacity: 0;
  animation: appear 2s forwards;
  animation-delay: 1s;
}

.from {
  margin-top: 20px;
  font-weight: bold;
  animation-delay: 2s;
}

/* 🎂 bougie */
.candle {
  width: 12px;
  height: 45px;
  background: repeating-linear-gradient(45deg, yellow, orange 5px);
  margin: 25px auto;
  position: relative;
  border-radius: 4px;
}

.flame {
  width: 14px;
  height: 20px;
  background: radial-gradient(circle, #ff0, orange, red);
  border-radius: 50%;
  position: absolute;
  top: -20px;
  left: -1px;
  animation: flicker 0.2s infinite alternate;
}

@keyframes flicker {
  from { transform: scale(1); opacity: 1; }
  to { transform: scale(1.3); opacity: 0.6; }
}

/* 🎊 confettis */
.confetti {
  position: absolute;
  width: 8px;
  height: 8px;
  top: -10px;
  animation: fall linear infinite;
}

@keyframes fall {
  to { transform: translateY(100vh) rotate(720deg); }
}

/* 💥 explosion */
.burst {
  position: absolute;
  width: 10px;
  height: 10px;
  background: white;
  border-radius: 50%;
  animation: explode 0.8s forwards;
}

@keyframes explode {
  to {
    transform: scale(10);
    opacity: 0;
  }
}

  </style>
</head>
<body>  <div class="gift" onclick="openGift(event)"></div>  <div class="content" id="content">
    <h1 id="title">🎂 Joyeux Anniversaire Maman 🎉</h1>
    <div class="date">Jeudi 23 Avril 2026</div>
    <div class="candle"><div class="flame"></div></div>
    <div class="from">❤️ De la part de Marwane, Manel et Yassine ❤️</div>
  </div>  <audio id="music" loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
  </audio>  <script>
    function openGift(e) {
      createExplosion(e.clientX, e.clientY);

      document.querySelector('.gift').style.display = 'none';
      document.getElementById('content').style.display = 'block';
      document.body.classList.add('party');

      document.getElementById('music').play();

      setInterval(createConfetti, 70);
    }

    function createConfetti() {
      const el = document.createElement('div');
      el.className = 'confetti';
      document.body.appendChild(el);

      el.style.left = Math.random() * window.innerWidth + 'px';
      el.style.backgroundColor = `hsl(${Math.random()*360},100%,50%)`;
      el.style.animationDuration = (Math.random()*3+2)+'s';

      setTimeout(() => el.remove(), 5000);
    }

    function createExplosion(x, y) {
      for (let i = 0; i < 20; i++) {
        const b = document.createElement('div');
        b.className = 'burst';
        document.body.appendChild(b);

        b.style.left = x + 'px';
        b.style.top = y + 'px';
        b.style.backgroundColor = `hsl(${Math.random()*360},100%,50%)`;

        setTimeout(() => b.remove(), 800);
      }
    }
  </script></body>
</html>
