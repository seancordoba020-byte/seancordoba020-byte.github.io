# seancordoba020-byte.github.io[index.html.txt](https://github.com/user-attachments/files/25000235/index.html.txt)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Will You Be My Valentine?</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      margin: 0;
      height: 100vh;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff758c, #ff7eb3);
      font-family: Arial, sans-serif;
      color: #fff;
    }

    .card {
      background: rgba(255,255,255,0.15);
      padding: 40px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0,0,0,0.25);
      z-index: 2;
    }

    h1 {
      margin-bottom: 30px;
      font-size: 2rem;
    }

    .buttons {
      position: relative;
      display: flex;
      gap: 20px;
      justify-content: center;
    }

    button {
      padding: 12px 30px;
      font-size: 1.1rem;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      background: #fff;
      color: #ff4f81;
      font-weight: bold;
      transition: transform 0.2s;
    }

    button:hover {
      transform: scale(1.1);
    }

    /* Floating hearts */
    .heart {
      position: absolute;
      font-size: 20px;
      animation: floatUp linear infinite;
      color: rgba(255,255,255,0.8);
    }

    @keyframes floatUp {
      0% {
        transform: translateY(100vh) scale(0.8);
        opacity: 0;
      }
      20% {
        opacity: 1;
      }
      100% {
        transform: translateY(-10vh) scale(1.2);
        opacity: 0;
      }
    }
  </style>
</head>

<body>

  <!-- Background music (autoplay after interaction) -->
  <audio id="bgMusic" loop>
    <source src="https://assets.mixkit.co/music/preview/mixkit-romantic-soft-piano-238.mp3" type="audio/mpeg">
  </audio>

  <!-- Click sound -->
  <audio id="loveSound">
    <source src="https://assets.mixkit.co/sfx/preview/mixkit-romantic-chime-1004.mp3" type="audio/mpeg">
  </audio>

  <div class="card">
    <h1>Will you be my Valentine, <span id="name">Carla</span>? 💘</h1>
    <p style="font-size:0.9rem; opacity:0.85;">🔊 Tap anywhere to play music</p>
    <div class="buttons">
      <button onclick="yes()">Yes</button>
      <button id="runaway">Yes</button>
    </div>
  </div>

  <script>
    const bgMusic = document.getElementById("bgMusic");

    // Start background music on first interaction (mobile-friendly)
    document.body.addEventListener("click", () => {
      if (bgMusic.paused) {
        bgMusic.volume = 0.4;
        bgMusic.play();
      }
    }, { once: true });

    function yes() {
      document.getElementById("loveSound").play();

      document.body.innerHTML = `
        <div style="
          height:100vh;
          display:flex;
          justify-content:center;
          align-items:center;
          background: linear-gradient(135deg, #ff758c, #ff7eb3);
          color:white;
          font-family:Arial, sans-serif;
          text-align:center;
          flex-direction:column;
        ">
          <h1>Yay! 💖</h1>
          <h2>Happy Valentine’s Day 😘</h2>
        </div>
      `;
    }

    // Runaway Yes button
    const runaway = document.getElementById("runaway");
    runaway.addEventListener("mouseenter", () => {
      const x = Math.random() * (window.innerWidth - runaway.offsetWidth);
      const y = Math.random() * (window.innerHeight - runaway.offsetHeight);
      runaway.style.position = "fixed";
      runaway.style.left = x + "px";
      runaway.style.top = y + "px";
    });

    runaway.addEventListener("click", yes);

    // Floating hearts
    setInterval(() => {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.innerHTML = "❤️";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = (3 + Math.random() * 3) + "s";
      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 6000);
    }, 300);
  </script>

</body>
</html>
