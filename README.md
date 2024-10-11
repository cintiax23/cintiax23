<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minha Pessoa Favorita</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }

        .heart {
            width: 100px;
            height: 100px;
            background-color: red;
            position: relative;
            transform: rotate(-45deg);
            animation: heartbeat 1s infinite;
        }

        .heart::before, .heart::after {
            content: "";
            width: 100px;
            height: 100px;
            background-color: red;
            border-radius: 50%;
            position: absolute;
        }

        .heart::before {
            top: -50px;
            left: 0;
        }

        .heart::after {
            left: 50px;
            top: 0;
        }

        @keyframes heartbeat {
            0%, 100% {
                transform: scale(1) rotate(-45deg);
            }
            50% {
                transform: scale(1.2) rotate(-45deg);
            }
        }

        .message {
            margin-top: 20px;
            font-size: 20px;
            text-align: center;
        }

        .buttons {
            margin-top: 20px;
        }

        button {
            padding: 10px 20px;
            font-size: 16px;
            margin: 5px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            transition: transform 0.2s;
        }

        #yesButton {
            background-color: green;
            color: white;
        }

        #noButton {
            background-color: red;
            color: white;
        }

        .hidden {
            display: none;
        }

        img {
            margin-top: 20px;
            width: 200px;
            height: auto;
            display: none;
        }
    </style>
</head>
<body>
    <div class="heart"></div>
    <div class="message">Você quer ser a minha pessoa favorita até o último dia da minha vida?</div>
    <div class="buttons">
        <button id="yesButton">Sim</button>
        <button id="noButton">Não</button>
    </div>
    <div id="loveMessage" class="hidden">Espero que tenha um ótimo dia, minha princesa! ❤️ Você é maravilhosa demais! A foto abaixo mostra como eu fiquei quando estava com você KKKKK. Você fez uma ótima escolha!</div>
    <img id="funnyImage" src="https://i.pinimg.com/236x/00/ae/f3/00aef3bf9cee1a0706b09c474b5f29eb.jpg" alt="Pica Pau apaixonado">
    
    <script>
        const yesButton = document.getElementById('yesButton');
        const noButton = document.getElementById('noButton');
        const loveMessage = document.getElementById('loveMessage');
        const funnyImage = document.getElementById('funnyImage');

        yesButton.addEventListener('click', () => {
            loveMessage.classList.remove('hidden');
            funnyImage.style.display = 'block';
            confettiExplosion();
        });

        noButton.addEventListener('mouseover', () => {
            const offsetX = Math.random() * 200 - 100;
            const offsetY = Math.random() * 200 - 100;
            noButton.style.transform = `translate(${offsetX}px, ${offsetY}px)`;
        });

        function confettiExplosion() {
            for (let i = 0; i < 100; i++) {
                createConfetti(i * 10);
            }
        }

        function createConfetti(delay) {
            setTimeout(() => {
                const confetti = document.createElement('div');
                confetti.innerHTML = '❤️';
                confetti.style.position = 'fixed';
                confetti.style.left = Math.random() * window.innerWidth + 'px';
                confetti.style.top = Math.random() * window.innerHeight + 'px';
                confetti.style.fontSize = '24px';
                document.body.appendChild(confetti);
                setTimeout(() => confetti.remove(), 3000);
            }, delay);
        }
    </script>
</body>
</html>


