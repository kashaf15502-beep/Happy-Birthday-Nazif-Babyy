<!--
Tom & Jerry — Happy Birthday Nazif
Single-file HTML animation. Save as "tom-and-jerry-birthday.html" and open in a browser.

Features:
- Simple stylized Tom (cat) and Jerry (mouse) using SVG shapes (not photo-realistic)
- Speech bubble: "Happy Birthday Nazif"
- A cake shaped like a car with 5 candles and the text "Happy Birthday Nazif" on it
- Dancing animation and candle flicker
- Plays a short chime (optional) when you click the cake

You can edit sizes, colors, and text inside the file.
-->

<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Happy Birthday Nazif — Tom & Jerry</title>
<style>
  :root{
    --bg:#f7f9fd;
    --floor:#e3eef8;
    --accent:#ff6b6b;
    --dark:#333;
  }
  html,body{height:100%;margin:0;font-family: 'Segoe UI', Roboto, Arial, sans-serif;background:linear-gradient(180deg,var(--bg),#e9f2ff);}
  .stage{height:100%;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:18px;padding:20px;box-sizing:border-box}
  .scene{width:920px;max-width:95%;height:500px;background:transparent;border-radius:18px;position:relative;overflow:visible}
  .floor{position:absolute;left:0;right:0;bottom:0;height:110px;background:var(--floor);border-radius:0 0 18px 18px}

  /* SVG container centering */
  svg{width:100%;height:100%;display:block}

  /* Dancing animations */
  .dance-tom{transform-origin:60% 85%;animation:tom-bop 1.1s ease-in-out infinite}
  .dance-jerry{transform-origin:40% 85%;animation:jerry-bop 0.9s ease-in-out infinite}

  @keyframes tom-bop{
    0%{transform:translateY(0) rotate(0deg)}
    25%{transform:translateY(-12px) rotate(-3deg)}
    50%{transform:translateY(0) rotate(0deg)}
    75%{transform:translateY(-8px) rotate(3deg)}
    100%{transform:translateY(0) rotate(0deg)}
  }
  @keyframes jerry-bop{
    0%{transform:translateY(0) rotate(0deg)}
    25%{transform:translateY(-8px) rotate(3deg)}
    50%{transform:translateY(0) rotate(0deg)}
    75%{transform:translateY(-6px) rotate(-3deg)}
    100%{transform:translateY(0) rotate(0deg)}
  }

  /* Speech bubble */
  .bubble{font-weight:700;fill:#fff;stroke:#ffd966;stroke-width:2;filter:drop-shadow(0 4px 6px rgba(0,0,0,0.08));}
  .bubble-text{font-size:28px;fill:#222;text-anchor:middle;font-family:inherit}

  /* Cake car and candles */
  .car-cake{cursor:pointer}
  .candles .flame{transform-origin:center bottom;animation:flicker 0.14s linear infinite}
  @keyframes flicker{
    0%{transform:translateY(0) scaleY(1)}
    50%{transform:translateY(-1px) scaleY(0.95)}
    100%{transform:translateY(0) scaleY(1)}
  }

  /* Wheels bobbing */
  .wheel{animation:wheel-bob 1.2s ease-in-out infinite}
  @keyframes wheel-bob{
    0%{transform:translateY(0)}
    50%{transform:translateY(-4px)}
    100%{transform:translateY(0)}
  }

  /* small UI */
  .controls{display:flex;gap:10px;align-items:center}
  .btn{background:#2b6df6;color:white;padding:8px 12px;border-radius:8px;border:0;cursor:pointer;font-weight:600}
  .credits{position:absolute;right:12px;top:12px;font-size:12px;color:#666}

  /* Responsive tweaks */
  @media (max-width:640px){
    .bubble-text{font-size:18px}
  }
</style>
</head>
<body>
  <div class="stage">
    <div class="scene" role="img" aria-label="Tom and Jerry dancing with a car-shaped cake saying Happy Birthday Nazif">
      <div class="credits">Click the cake to play chime</div>
      <svg viewBox="0 0 920 500" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid meet">
        <!-- Background sun / stage -->
        <defs>
          <linearGradient id="sky" x1="0" x2="0" y1="0" y2="1">
            <stop offset="0%" stop-color="#fff" stop-opacity="0.9"/>
            <stop offset="100%" stop-color="#d9efff"/>
          </linearGradient>
        </defs>
        <rect x="0" y="0" width="920" height="500" fill="url(#sky)" rx="18"/>

        <!-- Floor shape -->
        <rect x="0" y="390" width="920" height="110" fill="#eaf6ff" rx="0"/>

        <!-- Speech bubble -->
        <g transform="translate(460,70)">
          <path class="bubble" d="M-220 0 h380 a30 30 0 0 1 30 30 v40 a30 30 0 0 1 -30 30 h-300 l-40 40 v-40 h-40 a30 30 0 0 1 -30 -30 v-40 a30 30 0 0 1 30 -30 z"/>
          <text class="bubble-text" x="-30" y="55">Happy Birthday Nazif 🎉</text>
        </g>

        <!-- Tom (stylized cat) on right -->
        <g class="dance-tom" transform="translate(620,250) scale(0.95)">
          <!-- body -->
          <ellipse cx="0" cy="60" rx="68" ry="40" fill="#9ab7d8" stroke="#5d7b95" stroke-width="2"/>
          <!-- head -->
          <g transform="translate(0,-20)">
            <circle cx="0" cy="0" r="46" fill="#9ab7d8" stroke="#5d7b95" stroke-width="2"/>
            <!-- ears -->
            <path d="M-34,-18 L-52,-48 L-14,-36 Z" fill="#9ab7d8" stroke="#5d7b95" stroke-width="2"/>
            <path d="M34,-18 L52,-48 L14,-36 Z" fill="#9ab7d8" stroke="#5d7b95" stroke-width="2"/>
            <!-- face -->
            <ellipse cx="-14" cy="0" rx="10" ry="8" fill="#fff"/>
            <ellipse cx="14" cy="0" rx="10" ry="8" fill="#fff"/>
            <circle cx="-13" cy="0" r="3" fill="#222"/>
            <circle cx="13" cy="0" r="3" fill="#222"/>
            <path d="M-12,18 q12 14 36 0" stroke="#422" stroke-width="3" fill="none" stroke-linecap="round"/>
          </g>
          <!-- arms -->
          <rect x="-10" y="30" width="20" height="8" rx="4" fill="#9ab7d8" transform="rotate(-12)"/>
          <rect x="-10" y="30" width="20" height="8" rx="4" fill="#9ab7d8" transform="rotate(12)"/>
        </g>

        <!-- Jerry (stylized mouse) on left -->
        <g class="dance-jerry" transform="translate(220,260) scale(0.85)">
          <!-- body -->
          <ellipse cx="0" cy="60" rx="46" ry="30" fill="#e9c89f" stroke="#b98f63" stroke-width="2"/>
          <!-- head -->
          <g transform="translate(0,-18)">
            <circle cx="0" cy="0" r="34" fill="#e9c89f" stroke="#b98f63" stroke-width="2"/>
            <!-- ears -->
            <circle cx="-20" cy="-14" r="12" fill="#e9c89f" stroke="#b98f63" stroke-width="1.6"/>
            <circle cx="20" cy="-14" r="12" fill="#e9c89f" stroke="#b98f63" stroke-width="1.6"/>
            <!-- face -->
            <ellipse cx="-8" cy="0" rx="6" ry="5" fill="#fff"/>
            <ellipse cx="8" cy="0" rx="6" ry="5" fill="#fff"/>
            <circle cx="-8" cy="0" r="2.2" fill="#222"/>
            <circle cx="8" cy="0" r="2.2" fill="#222"/>
            <path d="M-10,18 q10 10 26 0" stroke="#6a3b1b" stroke-width="2" fill="none" stroke-linecap="round"/>
          </g>
          <!-- tail -->
          <path d="M40,70 q40 10 60 -10" stroke="#b98f63" stroke-width="6" stroke-linecap="round" fill="none"/>
        </g>

        <!-- Cake shaped like a car (center) -->
        <g id="cakeCar" class="car-cake" transform="translate(360,300) scale(1)">
          <!-- car body as cake -->
          <rect x="-130" y="-42" width="260" height="74" rx="16" ry="16" fill="#ffe9d6" stroke="#e6b89a" stroke-width="3"/>
          <!-- car top -->
          <rect x="-70" y="-78" width="140" height="48" rx="12" ry="12" fill="#fff3e8" stroke="#e6b89a" stroke-width="3"/>
          <!-- windows (icing) -->
          <rect x="-60" y="-70" width="50" height="34" rx="8" fill="#dbeeff" stroke="#b3d0ff"/>
          <rect x="10" y="-70" width="50" height="34" rx="8" fill="#dbeeff" stroke="#b3d0ff"/>

          <!-- wheels as cookies -->
          <g transform="translate(-70,36)" class="wheel">
            <circle r="26" fill="#6b4f3a"/>
            <circle r="12" fill="#f3c19a"/>
          </g>
          <g transform="translate(70,36)" class="wheel">
            <circle r="26" fill="#6b4f3a"/>
            <circle r="12" fill="#f3c19a"/>
          </g>

          <!-- cake writing -->
          <text x="0" y="-6" text-anchor="middle" font-family="inherit" font-weight="700" font-size="20" fill="#9a4d72">Happy Birthday Nazif</text>

          <!-- five candles on the top of the car-cake -->
          <g class="candles" transform="translate(-82,-86)">
            <!-- candles spaced -->
            <g transform="translate(0,0)">
              <rect x="0" y="0" width="8" height="28" rx="2" fill="#ffb6b6"/>
              <g transform="translate(4,-6)" class="flame">
                <path d="M0 0 q3 -6 0 -10 q-3 4 0 10 z" fill="#ffd34d"/>
              </g>
            </g>
            <g transform="translate(30,0)">
              <rect x="0" y="0" width="8" height="28" rx="2" fill="#ffd6a5"/>
              <g transform="translate(4,-6)" class="flame">
                <path d="M0 0 q3 -6 0 -10 q-3 4 0 10 z" fill="#ffd34d"/>
              </g>
            </g>
            <g transform="translate(60,0)">
              <rect x="0" y="0" width="8" height="28" rx="2" fill="#bfe6a9"/>
              <g transform="translate(4,-6)" class="flame">
                <path d="M0 0 q3 -6 0 -10 q-3 4 0 10 z" fill="#ffd34d"/>
              </g>
            </g>
            <g transform="translate(90,0)">
              <rect x="0" y="0" width="8" height="28" rx="2" fill="#c3d4ff"/>
              <g transform="translate(4,-6)" class="flame">
                <path d="M0 0 q3 -6 0 -10 q-3 4 0 10 z" fill="#ffd34d"/>
              </g>
            </g>
            <g transform="translate(120,0)">
              <rect x="0" y="0" width="8" height="28" rx="2" fill="#ffd6ea"/>
              <g transform="translate(4,-6)" class="flame">
                <path d="M0 0 q3 -6 0 -10 q-3 4 0 10 z" fill="#ffd34d"/>
              </g>
            </g>
          </g>

        </g>

        <!-- little confetti dots -->
        <g id="confetti">
          <!-- generate several circles -->
          <circle cx="120" cy="110" r="4" fill="#ff7b7b" opacity="0.95"/>
          <circle cx="200" cy="60" r="5" fill="#ffd36b" opacity="0.9"/>
          <circle cx="320" cy="120" r="3.5" fill="#9ad08a"/>
          <circle cx="540" cy="40" r="4" fill="#9ad0ff"/>
          <circle cx="760" cy="120" r="4" fill="#d5a9ff"/>
        </g>

      </svg>
    </div>

    <div class="controls">
      <button id="blowBtn" class="btn">Blow Candles (Hide flames)</button>
      <button id="resetBtn" class="btn">Reset</button>
    </div>
  </div>

<script>
  // Basic interactivity: click cake to play a short chime and toggle flame visibility
  const cake = document.getElementById('cakeCar');
  const blowBtn = document.getElementById('blowBtn');
  const resetBtn = document.getElementById('resetBtn');
  let flamesOn = true;

  // simple chime generated with WebAudio API
  function playChime(){
    try{
      const ctx = new (window.AudioContext || window.webkitAudioContext)();
      const o = ctx.createOscillator();
      const g = ctx.createGain();
      o.type = 'triangle';
      o.frequency.value = 880;
      o.connect(g);
      g.connect(ctx.destination);
      g.gain.value = 0.0001;
      const now = ctx.currentTime;
      g.gain.exponentialRampToValueAtTime(0.1, now + 0.02);
      o.start(now);
      o.frequency.exponentialRampToValueAtTime(660, now + 0.2);
      g.gain.exponentialRampToValueAtTime(0.0001, now + 1.2);
      o.stop(now + 1.25);
    }catch(e){
      console.warn('Audio failed:', e);
    }
  }

  function setFlames(on){
    document.querySelectorAll('.candles .flame').forEach(el=>{
      el.style.display = on ? 'block' : 'none';
    });
    flamesOn = on;
    blowBtn.textContent = on ? 'Blow Candles (Hide flames)' : 'Relight Candles';
  }

  cake.addEventListener('click', ()=>{
    playChime();
    // small confetti burst animation
    burstConfetti();
  });

  blowBtn.addEventListener('click', ()=>{
    setFlames(!flamesOn);
  });

  resetBtn.addEventListener('click', ()=>{
    setFlames(true);
    // tiny nudge to dancers
    document.querySelector('.dance-tom').style.animation = 'none';
    document.querySelector('.dance-jerry').style.animation = 'none';
    void document.querySelector('.dance-tom').offsetWidth;
    document.querySelector('.dance-tom').style.animation = '';
    document.querySelector('.dance-jerry').style.animation = '';
  });

  // confetti burst function (simple SVG circles expanding)
  function burstConfetti(){
    const svg = document.querySelector('svg');
    for(let i=0;i<18;i++){
      const c = document.createElementNS('http://www.w3.org/2000/svg','circle');
      const startX = 360 + Math.random()*160 - 80; // around cake
      const startY = 220 + Math.random()*40 - 20;
      c.setAttribute('cx', startX);
      c.setAttribute('cy', startY);
      c.setAttribute('r', 5 + Math.random()*5);
      const colors = ['#ff7b7b','#ffd36b','#9ad08a','#9ad0ff','#d5a9ff'];
      c.setAttribute('fill', colors[Math.floor(Math.random()*colors.length)]);
      c.style.opacity = '1';
      svg.appendChild(c);
      // animate using setInterval (small and simple)
      const vx = (Math.random()-0.5)*10;
      const vy = (Math.random()-1.2)*10;
      let ticks = 0;
      const id = setInterval(()=>{
        ticks++;
        const cx = parseFloat(c.getAttribute('cx')) + vx*0.08;
        const cy = parseFloat(c.getAttribute('cy')) + vy*0.08 + ticks*0.08;
        c.setAttribute('cx',cx);
        c.setAttribute('cy',cy);
        c.style.opacity = Math.max(0, 1 - ticks/30);
        if(ticks>40){ clearInterval(id); c.remove(); }
      }, 16);
    }
  }

  // start with flames visible
  setFlames(true);
</script>
</body>
</html>
