<!DOCTYPE html><html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🎁 Surprise Maman</title>
<style>
body {
  margin:0;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background: radial-gradient(circle at top, #1a1a1a, #000);
  overflow:hidden;
  font-family:sans-serif;
}/* 🎁 cadeau */ .gift { width:160px; height:160px; position:relative; cursor:pointer; transform: perspective(800px) rotateX(10deg); animation: float 2s infinite ease-in-out; }

.box { width:100%; height:100%; background: linear-gradient(145deg, #ff2e2e, #990000); border-radius:12px; position:absolute; box-shadow: 0 25px 50px rgba(0,0,0,0.7); }

.ribbon-vertical { position:absolute; width:25px; height:100%; left:50%; transform:translateX(-50%); background:gold; }

.ribbon-horizontal { position:absolute; height:25px; width:100%; top:50%; transform:translateY(-50%); background:gold; }

.lid { width:160px; height:50px; background: linear-gradient(145deg, #ff4d4d, #800000); position:absolute; top:-50px; left:0; border-radius:12px 12px 0 0; transform-origin:bottom; box-shadow:0 15px 25px rgba(0,0,0,0.6); }

@keyframes openLid { to { transform: rotateX(-140deg) translateY(-20px); } }

@keyframes float { 0%,100% { transform: perspective(800px) rotateX(10deg) translateY(0); } 50% { transform: perspective(800px) rotateX(10deg) translateY(-12px); } }

/* 🎉 contenu */ .content { display:none; position:absolute; text-align:center; color:white; padding:20px; backdrop-filter: blur(6px); }

h1 { font-size:clamp(2em,7vw,3.5em); opacity:0; animation: fadeIn 2s forwards; text-shadow:0 0 20px rgba(255,255,255,0.5); }

@keyframes fadeIn { to {opacity:1; transform:translateY(-10px)} }

/* 🎂 bougie améliorée */ .candle { width:14px; height:50px; background: repeating-linear-gradient(45deg, #fff, #ffd700 5px); margin:25px auto; position:relative; border-radius:4px; }

.flame { width:16px; height:22px; background: radial-gradient(circle, #ffff66, orange, red); border-radius:50%; position:absolute; top:-22px; left:-1px; animation:flicker .15s infinite alternate; box-shadow:0 0 20px orange; }

@keyframes flicker { from{transform:scale(1);opacity:1} to{transform:scale(1.3);opacity:.6} }

.confetti { position:absolute; width:6px; height:6px; top:-10px; animation:fall linear infinite; }

@keyframes fall { to{transform:translateY(100vh) rotate(720deg)} }

.balloon { position:absolute; bottom:-100px; width:30px; height:40px; border-radius:50%; animation: rise 6s linear infinite; }

@keyframes rise { to{transform:translateY(-120vh)} }

.firework { position:absolute; width:5px; height:5px; border-radius:50%; animation: explode 1s forwards; }

@keyframes explode { to { transform: scale(15); opacity:0; } }

</style>
</head>
<body><div class="gift" onclick="openGift(event)">
  <div class="lid" id="lid"></div>
  <div class="box"></div>
  <div class="ribbon-vertical"></div>
  <div class="ribbon-horizontal"></div>
</div><div class="content" id="content">
  <h1>🎂 Joyeux Anniversaire Maman 🎉</h1>
  <div>Jeudi 23 Avril 2026</div>
  <div class="candle"><div class="flame"></div></div>
  <div>❤️ De la part de Marwane, Manel Yassine et Papa ❤️</div>
</div><!-- 🎵 musique corrigée fiable --><audio id="music" preload="auto">
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c8a1a2d2a6.mp3" type="audio/mpeg">
</audio><script>
function openGift(e){
  document.getElementById('lid').style.animation='openLid 0.8s forwards';

  setTimeout(()=>{
    document.querySelector('.gift').style.display='none';
    document.getElementById('content').style.display='block';

    const music = document.getElementById('music');
    music.currentTime = 0;
    music.play().catch(()=>{});

    setInterval(confetti,80);
    setInterval(balloon,700), 
    setInterval(firework,1200);
  },700);
}

function confetti(){
  const el=document.createElement('div');
  el.className='confetti';
  document.body.appendChild(el);
  el.style.left=Math.random()*window.innerWidth+'px';
  el.style.backgroundColor=`hsl(${Math.random()*360},100%,50%)`;
  el.style.animationDuration=(Math.random()*3+2)+'s';
  setTimeout(()=>el.remove(),5000);
}

function balloon(){
  const b=document.createElement('div');
  b.className='balloon';
  document.body.appendChild(b);
  b.style.left=Math.random()*window.innerWidth+'px';
  b.style.backgroundColor=`hsl(${Math.random()*360},100%,60%)`;
  b.style.animationDuration=(Math.random()*3+4)+'s';
  setTimeout(()=>b.remove(),7000);
}

function firework(){
  const f=document.createElement('div');
  f.className='firework';
  document.body.appendChild(f);
  f.style.left=Math.random()*window.innerWidth+'px';
  f.style.top=Math.random()*window.innerHeight+'px';
  f.style.backgroundColor=`hsl(${Math.random()*360},100%,50%)`;
  setTimeout(()=>f.remove(),1000);
}
</script></body>
</html>
