<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

    body {
      margin: 0;
      height: 100vh;
      background-color: black;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      font-family: 'Creepster', cursive;
    }

    /* Calabaza fosforescente */
    .pumpkin {
      position: relative;
      width: 300px;
      height: 300px;
      background: radial-gradient(circle at center, orange 0%, #ff6600 80%);
      border-radius: 50%;
      box-shadow: 0 0 60px 20px rgba(255, 165, 0, 0.8);
      animation: glow 2s infinite alternate;
      z-index: 2;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    /* Segmentos de calabaza */
    .pumpkin::before, .pumpkin::after {
      content: '';
      position: absolute;
      top: 50%;
      width: 40px;
      height: 100px;
      background: #ff6600;
      border-radius: 50%;
      transform: translateY(-50%);
    }

    .pumpkin::before { left: -20px; }
    .pumpkin::after { right: -20px; }

    /* Tallo */
    .stem {
      position: absolute;
      top: -40px;
      left: 50%;
      transform: translateX(-50%);
      width: 40px;
      height: 60px;
      background: green;
      border-radius: 10px;
    }

    /* Animación brillo */
    @keyframes glow {
      from { box-shadow: 0 0 40px 10px rgba(255, 165, 0, 0.5); }
      to { box-shadow: 0 0 80px 30px rgba(255, 255, 0, 1); }
    }

    /* Cara de calabaza */
    .face {
      position: absolute;
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    .eyes {
      display: flex;
      justify-content: space-between;
      width: 55%;
      margin-bottom: 10px;
    }

    .eye {
      width: 60px;
      height: 60px;
      background: black;
      clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
      box-shadow: 0 0 20px 10px rgba(0,0,0,0.8);
    }

    .nose {
      width: 30px;
      height: 30px;
      background: black;
      clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
      margin: 5px 0 15px 0;
    }

    .mouth {
      width: 180px;
      height: 80px;
      background: black;
      clip-path: polygon(0% 50%, 10% 70%, 20% 40%, 30% 70%, 40% 45%, 50% 75%, 
                        60% 45%, 70% 70%, 80% 40%, 90% 70%, 100% 50%, 100% 100%, 0% 100%);
      box-shadow: 0 0 25px 12px rgba(0,0,0,0.8);
    }

    /* Texto */
    .message {
      position: absolute;
      bottom: 30px;
      text-align: center;
      font-size: 2rem;
      color: #ff66ff;
      text-shadow: 0 0 15px #ff33ff, 0 0 30px #ff00ff;
      animation: floatText 3s ease-in-out infinite;
    }

    @keyframes floatText {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    /* Murciélagos */
    .bat {
      position: absolute;
      width: 60px;
      height: 20px;
      background: black;
      border-radius: 50% 50% 0 0;
      animation: fly 10s linear infinite;
      opacity: 0.8;
    }

    .bat::before, .bat::after {
      content: '';
      position: absolute;
      width: 30px;
      height: 20px;
      background: black;
      border-radius: 50%;
      top: 0;
    }

    .bat::before { left: -30px; }
    .bat::after { right: -30px; }

    @keyframes fly {
      0% { transform: translateX(-10vw) translateY(0); }
      50% { transform: translateX(50vw) translateY(-15vh); }
      100% { transform: translateX(110vw) translateY(0); }
    }

    /* Luces flotantes */
    .light {
      position: absolute;
      width: 6px;
      height: 6px;
      background: #ffff99;
      border-radius: 50%;
      box-shadow: 0 0 10px 5px #ffff66;
      animation: floatLight 6s ease-in-out infinite;
    }

    @keyframes floatLight {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      50% { transform: translateY(-50px) scale(1.2); opacity: 0.6; }
      100% { transform: translateY(0) scale(1); opacity: 1; }
    }
  </style>
</head>
<body>
  <div class="pumpkin">
    <div class="stem"></div>
    <div class="face">
      <div class="eyes">
        <div class="eye"></div>
        <div class="eye"></div>
      </div>
      <div class="nose"></div>
      <div class="mouth"></div>
    </div>
  </div>

  <div class="message">Boo! Te quiero tanto que hasta los fantasmas se ponen celosos 👻💜</div>

  <!-- Murciélagos extra -->
  <div class="bat" style="top:15%; animation-delay:0s;"></div>
  <div class="bat" style="top:30%; animation-delay:2s;"></div>
  <div class="bat" style="top:45%; animation-delay:4s;"></div>
  <div class="bat" style="top:60%; animation-delay:6s;"></div>
  <div class="bat" style="top:75%; animation-delay:8s;"></div>

  <!-- Luces flotantes -->
  <script>
    for (let i = 0; i < 25; i++) {
      let light = document.createElement("div");
      light.className = "light";
      light.style.left = Math.random() * 100 + "vw";
      light.style.top = Math.random() * 100 + "vh";
      light.style.animationDuration = (4 + Math.random() * 4) + "s";
      document.body.appendChild(light);
    }
 
