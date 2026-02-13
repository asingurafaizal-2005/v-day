<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Fama... My Forever Friend? 💕</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      color: #fff;
      overflow: hidden;
      text-align: center;
    }
    h1 {
      font-size: 3.8rem;
      margin: 20px;
      text-shadow: 0 0 20px rgba(255,255,255,0.9);
      animation: pulse 2.8s infinite;
    }
    .gif {
      max-width: 320px;
      margin: 25px 0;
      border-radius: 25px;
      box-shadow: 0 12px 35px rgba(0,0,0,0.4);
    }
    .buttons {
      margin-top: 40px;
    }
    button {
      padding: 20px 60px;
      font-size: 1.8rem;
      margin: 20px;
      border: none;
      border-radius: 60px;
      cursor: pointer;
      transition: all 0.4s ease;
      box-shadow: 0 10px 25px rgba(0,0,0,0.4);
    }
    #yesBtn {
      background: #ff4757;
      color: white;
    }
    #noBtn {
      background: #57606f;
      color: white;
    }
    #yesBtn:hover { transform: scale(1.12); background: #ff6b81; }
    #noBtn:hover { transform: scale(1.12); background: #747d8c; }
    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.1); }
    }
    .heart-rain {
      position: absolute;
      top: -20px;
      width: 100%;
      height: 100%;
      pointer-events: none;
      overflow: hidden;
      z-index: -1;
    }
    .heart-rain span {
      position: absolute;
      color: #fff;
      font-size: 2.5rem;
      animation: fall linear infinite;
      opacity: 0.85;
    }
    @keyframes fall {
      to { transform: translateY(130vh) rotate(1080deg); }
    }
  </style>
</head>
<body>
  <div class="heart-rain" id="hearts"></div>

  <h1 id="question">FAMA WILL YOU BE MY FOREVER FRIEND...</h1>
  
  <img class="gif" id="gif" src="https://media.tenor.com/EBV7OT7ACfwAAAAj/u-u-qua-qua-u-quaa.gif" alt="cute shy character">

  <div class="buttons">
    <button id="yesBtn">Yes</button>
    <button id="noBtn">No</button>
  </div>

  <script>
    const question = document.getElementById('question');
    const gif = document.getElementById('gif');
    const yesBtn = document.getElementById('yesBtn');
    const noBtn = document.getElementById('noBtn');
    const heartsContainer = document.getElementById('hearts');

    let noCount = 0;
    const noPhrases = [
      "Think again, Fama? 😏",
      "Come on... pretty please? 🥺",
      "My heart is glitching without you 💔",
      "One more chance? 😭",
      "Don't leave me hanging... 😔",
      "Okay but I'm not giving up! ❤️"
    ];

    function createHeart() {
      const heart = document.createElement('span');
      heart.innerHTML = Math.random() > 0.5 ? '❤️' : '💕';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = (Math.random() * 4 + 5) + 's';
      heart.style.fontSize = (Math.random() * 2 + 1.5) + 'rem';
      heartsContainer.appendChild(heart);
      setTimeout(() => heart.remove(), 8000);
    }

    function startHeartRain() {
      const interval = setInterval(createHeart, 150);
      setTimeout(() => clearInterval(interval), 6000); // rain for ~6s
    }

    noBtn.addEventListener('click', () => {
      noCount++;
      noBtn.style.transform = `scale(${1 + noCount * 0.15})`;
      noBtn.style.opacity = Math.max(0.3, 1 - noCount * 0.12);
      
      if (noCount < noPhrases.length) {
        question.textContent = noPhrases[noCount];
      } else {
        question.textContent = "Fine... but I'll keep asking forever! 😘";
      }

      // Optional: swap to sadder GIF if you want
      // gif.src = "https://media.tenor.com/some-sad-cute.gif";
    });

    yesBtn.addEventListener('click', () => {
      startHeartRain();
      question.innerHTML = "YAY! 💕<br>LET'S BE KISSING FOREVER 😘💋";
      gif.src = "https://media.tenor.com/3PvUFBvriI8AAAAC/kiss-kissing.gif"; // romantic kissing GIF
      yesBtn.style.display = 'none';
      noBtn.style.display = 'none';
      
      // Extra fun: keep hearts going longer
      setInterval(createHeart, 300);
    });
  </script>
</body>
</html>
