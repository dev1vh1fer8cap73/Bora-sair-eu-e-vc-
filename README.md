<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
  body {
    margin: 0;
    padding: 0;
    background-color: black;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    font-family: Arial, sans-serif;
    color: white;
    overflow: hidden; /* Evita barras de rolagem */
  }
  
  #container {
    text-align: center;
  }
  
  h2 {
    font-size: 24px;
  }
  
  .button {
    background-color: white;
    color: blue;
    border: none;
    border-radius: 10px;
    padding: 10px 20px;
    margin: 10px;
    cursor: pointer;
  }

  .confetti {
    position: absolute;
    width: 10px;
    height: 10px;
    background-color: #f6d258;
    border-radius: 50%;
    pointer-events: none;
    opacity: 0;
    transform: rotate(45deg);
    animation: confetti-fall 4s ease-in-out infinite;
  }

  @keyframes confetti-fall {
    0%, 100% {
      transform: translateY(0) rotate(45deg);
      opacity: 1;
    }
    50% {
      transform: translateY(100vh) rotate(45deg);
      opacity: 0.5;
    }
  }
</style>
</head>
<body>
  <div id="container">
    <h2>Vamos sair?</h2>
    <button class="button" id="yesButton">Sim</button>
    <button class="button" id="noButton">Não</button>
  </div>

  <script>
    const yesButton = document.getElementById("yesButton");
    const noButton = document.getElementById("noButton");

    yesButton.addEventListener("click", () => {
      createConfetti();
    });

    noButton.addEventListener("mouseover", () => {
      const randomX = Math.random() * (window.innerWidth - 100);
      const randomY = Math.random() * (window.innerHeight - 50);

      noButton.style.position = "absolute";
      noButton.style.left = `${randomX}px`;
      noButton.style.top = `${randomY}px`;
    });

    function createConfetti() {
      const confettiCount = 100;
      const container = document.body;
      
      for (let i = 0; i < confettiCount; i++) {
        const confetti = document.createElement("div");
        confetti.className = "confetti";
        confetti.style.left = `${Math.random() * 100}vw`;
        confetti.style.animationDelay = `${Math.random() * 2}s`;
        container.appendChild(confetti);
        
        confetti.addEventListener("animationend", () => {
          confetti.remove();
        });
      }
    }
  </script>
</body>
</html>
