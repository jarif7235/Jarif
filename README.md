<!DOCTYPE html><html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Birthday Roast Page 🎂🔥</title>
  <style>
    body{
      margin:0;
      font:16px/1.5 system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
      background: linear-gradient(135deg,#ffdde1,#ee9ca7);
      color:#222;
      overflow-x:hidden;
    }
    .container{display:grid;place-items:center;min-height:100vh;padding:32px}
    .card{
      width:min(800px,90vw);
      background:#fff9;
      backdrop-filter: blur(6px);
      border-radius:28px;
      box-shadow:0 10px 30px rgba(0,0,0,.15);
      padding:28px;
      text-align:center;
      position:relative;
    }
    h1{font-size:clamp(28px,5vw,46px);margin:0 0 12px}
    .sub{opacity:.7;margin-bottom:20px}
    button{
      border:0;cursor:pointer;padding:14px 18px;border-radius:14px;font-weight:700;
      background:#ff3e3e;color:#fff;margin:6px;box-shadow:0 6px 16px rgba(0,0,0,.2);
      transition:transform .08s ease;
    }
    button:hover{transform:scale(1.05)}
    .panel{background:#fff;border-radius:18px;padding:18px;box-shadow:inset 0 0 0 2px #0001;margin:20px 0}
    .roast{font-size:clamp(18px,2.4vw,22px)}
    .cake{font-size:64px;animation:bounce 1.4s infinite alternate ease-in-out;}
    @keyframes bounce{to{transform:translateY(-16px)}}
    footer{text-align:center;opacity:.6;font-size:14px;margin-top:16px}
    .toast{ position:fixed; left:50%; bottom:18px; transform:translateX(-50%) translateY(120%);
      background:#111; color:#fff; padding:12px 16px; border-radius:12px; box-shadow:0 8px 22px rgba(0,0,0,.3);
      transition: transform .35s ease; z-index:5; }
    .toast.show{ transform:translateX(-50%) translateY(0) }
  </style>
</head>
<body>
  <div class="container">
    <div class="card">
      <h1>🎂 Happy Birthday… Sort of 🔥</h1>
      <p class="sub">Welcome to your official roast session. Don’t worry, we still love you… mostly.</p>
      <div class="cake">🎂</div>
      <section class="panel">
        <p id="roast" class="roast">Click a button to reveal how old you *really* are…</p>
        <button onclick="newRoast()">🔥 Roast Me</button>
        <button onclick="party()">🎉 Throw Confetti</button>
      </section>
      <footer>Made with love & sarcasm © <span id="year"></span></footer>
      <div class="toast" id="toast"></div>
    </div>
  </div>  <script>
    document.getElementById('year').textContent = new Date().getFullYear();

    const roasts = [
      "Another year older, still no sign of maturity!",
      "Congrats on leveling up! Too bad it’s in wrinkles.",
      "Happy Birthday! Don’t worry, your secrets are safe with us… we can’t remember them either.",
      "Age is just a number… but wow, yours is getting really high.",
      "You’re not old. You’re just… vintage. Like expired milk vintage.",
      "At least you’re not as old as you’ll be next year!",
      "Happy Birthday! Time to start lying about your age professionally."
    ];

    function newRoast(){
      const r = roasts[Math.floor(Math.random()*roasts.length)];
      document.getElementById('roast').textContent = r;
      showToast("🔥 Burn delivered!");
    }

    function party(){
      for(let i=0;i<60;i++){
        const c=document.createElement('div');
        c.textContent = ['🎉','🥳','🎂','🍰'][Math.floor(Math.random()*4)];
        c.style.position='fixed';
        c.style.left=Math.random()*100+'vw';
        c.style.top='-20px';
        c.style.fontSize= (20+Math.random()*20)+'px';
        c.style.animation=`fall ${3+Math.random()*2}s linear forwards`;
        document.body.appendChild(c);
        c.animate([{transform:'translateY(0)'},{transform:'translateY(110vh)'}],{duration:3000+Math.random()*2000,easing:'linear'}).onfinish=()=>c.remove();
      }
    }

    const toast = document.getElementById('toast');
    let toastTimer;
    function showToast(msg){
      toast.textContent = msg;
      toast.classList.add('show');
      clearTimeout(toastTimer);
      toastTimer = setTimeout(()=> toast.classList.remove('show'), 2000);
    }
  </script></body>
</html>
