# index
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Joguinho do Amor</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background-color: #fbe7c6;
      margin: 0;
      padding: 0;
      overflow: hidden;
    }

    .container {
      margin-top: 20%;
    }

    h1 {
      color: #ff6f61;
    }

    p {
      font-size: 1.5rem;
      color: #444;
    }

    .buttons {
      margin-top: 20px;
    }

    button {
      font-size: 1.2rem;
      padding: 10px 20px;
      margin: 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    #yes-btn {
      background-color: #4CAF50;
      color: white;
    }

    #yes-btn:hover {
      background-color: #45a049;
    }

    #no-btn {
      background-color: #f44336;
      color: white;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }

    #fireworks-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 999;
    }

    .firework {
      position: absolute;
      width: 10px;
      height: 10px;
      background-color: #ff0000;
      border-radius: 50%;
      box-shadow: 0 0 10px 2px #ff0000;
      animation: explode 1.5s ease-out;
    }

    @keyframes explode {
      0% {
        transform: scale(1);
        opacity: 1;
      }
      100% {
        transform: scale(3);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Oii meu amor! Estou pensando em você!</h1>
    <p>Vai ter c# hoje?</p>
    <div class="buttons">
      <button id="yes-btn">Sim</button>
      <button id="no-btn">Não</button>
    </div>
  </div>
  <div id="fireworks-container"></div>

  <script>
    const noBtn = document.getElementById('no-btn');
    const yesBtn = document.getElementById('yes-btn');
    const fireworksContainer = document.getElementById('fireworks-container');

    // Movimento do botão "Não"
    noBtn.addEventListener('mouseover', () => {
      const randomX = Math.random() * (window.innerWidth - 100); // Garantir que o botão não saia da tela
      const randomY = Math.random() * (window.innerHeight - 50);
      noBtn.style.left = `${randomX}px`;
      noBtn.style.top = `${randomY}px`;
    });

    // Ação do botão "Sim"
    yesBtn.addEventListener('click', () => {
      showFireworks();
      setTimeout(() => alert('Deixa de ser saliente!'), 1000); // Mensagem aparece com um leve atraso
    });

    // Função para mostrar fogos de artifício
    function showFireworks() {
      for (let i = 0; i < 20; i++) {
        const firework = document.createElement('div');
        firework.className = 'firework';
        fireworksContainer.appendChild(firework);

        const x = Math.random() * window.innerWidth;
        const y = Math.random() * window.innerHeight;

        firework.style.left = `${x}px`;
        firework.style.top = `${y}px`;

        setTimeout(() => {
          firework.remove();
        }, 1500);
      }
    }
  </script>
</body>
</html>
