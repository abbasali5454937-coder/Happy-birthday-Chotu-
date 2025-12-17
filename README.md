<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Abia! 🎉</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');

body {
  margin: 0;
  padding: 0;
  font-family: 'Pacifico', cursive;
  background: linear-gradient(to bottom, #ffe6f2, #ffb3d9);
  overflow: hidden;
  text-align: center;
  position: relative;
}

h1 {
  font-size: 2.5rem;
  color: #ff3399;
  margin-top: 20px;
  animation: bounce 2s infinite;
  text-shadow: 2px 2px #fff;
}

p {
  font-size: 1.2rem;
  margin: 10px 20px;
  color: #660033;
}

button {
  padding: 10px 20px;
  margin: 10px;
  font-size: 1rem;
  cursor: pointer;
  border-radius: 10px;
  border: none;
  background-color: #ff66cc;
  color: white;
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
  40% { transform: translateY(-10px); }
  60% { transform: translateY(-5px); }
}

/* Balloon style */
.balloon {
  position: absolute;
  width: 50px;
  height: 70px;
  border-radius: 50%;
  cursor: pointer;
  user-select: none;
}

/* Confetti */
.confetti {
  position: fixed;
  top: 0;
  width: 8px;
  height: 8px;
  opacity: 0.8;
  border-radius: 50%;
  animation: fall linear infinite;
}

@keyframes fall {
  0% { transform: translateY(-10px) rotate(0deg); }
  100% { transform: translateY(100vh) rotate(360deg); }
}

/* Star style */
.star {
  position: absolute;
  width: 20px;
  height: 20px;
  background: gold;
  clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
  cursor: pointer;
  user-select: none;
}

</style>
</head>
<body>

<h1>🎉 Happy 13th Birthday Abia! 🎉</h1>
<p>Tap the buttons below to play fun birthday games! 🎈</p>

<button onclick="startBalloons()">Pop the Balloons</button>
<button onclick="startStars()">Catch the Stars</button>
<button onclick="startGifts()">Click the Gifts</button>

<p>Score: <span id="score">0</span></p>

<script>
let score = 0;
const colors = ['#ff3399','#ff66cc','#ff99cc','#ffccff','#ff0066','#ff66ff','#ff99ff','#ffb3e6'];

// Remove old balloons/stars
function clearGame() {
  document.querySelectorAll('.balloon,.star,.gift').forEach(e=>e.remove());
}

// Add confetti
function addConfetti() {
  for(let i=0;i<50;i++){
    let c = document.createElement('div');
    c.classList.add('confetti');
    c.style.left = Math.random()*window.innerWidth + 'px';
    c.style.backgroundColor = colors[Math.floor(Math.random()*colors.length)];
    c.style.width = c.style.height = Math.random()*10+5+'px';
    c.style.animationDuration = Math.random()*3+2+'s';
    document.body.appendChild(c);
  }
}

// --- BALLOON GAME ---
function startBalloons(){
  clearGame();
  score=0; document.getElementById('score').innerText = score;
  addConfetti();

  for(let i=0;i<15;i++){
    let b = document.createElement('div');
    b.classList.add('balloon');
    b.style.left = Math.random()*window.innerWidth + 'px';
    b.style.bottom = '-100px';
    b.style.background = `radial-gradient(circle at 30% 30%, ${colors[Math.floor(Math.random()*colors.length)]}, #fff)`;
    document.body.appendChild(b);

    let speed = 2000 + Math.random()*3000;
    let bottom = -100;
    let id = setInterval(()=>{
      bottom += 2;
      b.style.bottom = bottom+'px';
      if(bottom>window.innerHeight+100){ clearInterval(id); b.remove(); }
    },speed/1000);

    b.addEventListener('click', ()=>{
      b.remove();
      score += 10;
      document.getElementById('score').innerText = score;
    });
  }
}

// --- STAR GAME ---
function startStars(){
  clearGame();
  score=0; document.getElementById('score').innerText = score;
  addConfetti();

  for(let i=0;i<20;i++){
    let s = document.createElement('div');
    s.classList.add('star');
    s.style.left = Math.random()*window.innerWidth + 'px';
    s.style.top = '-30px';
    document.body.appendChild(s);

    let speed = 2000 + Math.random()*2000;
    let top = -30;
    let id = setInterval(()=>{
      top += 2;
      s.style.top = top+'px';
      if(top>window.innerHeight+30){ clearInterval(id); s.remove(); }
    },speed/1000);

    s.addEventListener('click', ()=>{
      s.remove();
      score += 15;
      document.getElementById('score').innerText = score;
    });
  }
}

// --- GIFTS GAME ---
function startGifts(){
  clearGame();
  score=0; document.getElementById('score').innerText = score;
  addConfetti();

  for(let i=0;i<10;i++){
    let g = document.createElement('div');
    g.classList.add('gift');
    g.style.position='absolute';
    g.style.left = Math.random()*window.innerWidth+'px';
    g.style.top = Math.random()*window.innerHeight+'px';
    g.style.width='50px';
    g.style.height='50px';
    g.style.background = colors[Math.floor(Math.random()*colors.length)];
    g.style.borderRadius='10px';
    g.style.cursor='pointer';
    document.body.appendChild(g);

    g.addEventListener('click', ()=>{
      g.remove();
      score += 20;
      document.getElementById('score').innerText = score;
      let msg = document.createElement('p');
      msg.innerText = '🎁 Surprise! 🎁';
      msg.style.color = colors[Math.floor(Math.random()*colors.length)];
      msg.style.fontSize='1.2rem';
      document.body.appendChild(msg);
      setTimeout(()=>msg.remove(),1000);
    });
  }
}

</script>

</body>
</html>
