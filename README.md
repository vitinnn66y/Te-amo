<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Você Me Ama?</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5e1ee;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        /* Fundo com emojis repetidos */
        body::before {
            content: '🫶🏽❤️';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            font-size: 40px;
            line-height: 80px;
            opacity: 0.2;
            background: linear-gradient(rgba(255, 255, 255, 0.5), rgba(255, 255, 255, 0.5));
            background-image: repeating-linear-gradient(45deg, transparent, transparent 50px, rgba(255, 255, 255, 0.1) 50px, rgba(255, 255, 255, 0.1) 100px);
            z-index: -1;
            pointer-events: none;
        }
        .container {
            background-color: rgba(255, 255, 255, 0.9);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
            max-width: 600px;
            z-index: 1;
        }
        h1 {
            color: #e91e63;
            font-size: 36px;
            margin-bottom: 40px;
        }
        .buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
        }
        button {
            padding: 15px 30px;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        #yesBtn {
            background-color: #e91e63;
            color: white;
        }
        #yesBtn:hover {
            background-color: #d81b60;
        }
        #noBtn {
            background-color: #555;
            color: white;
            position: relative;
            z-index: 2; /* Garante que o botão fique acima do fundo */
        }
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Você me ama?</h1>
        <div class="buttons">
            <button id="yesBtn">Sim</button>
            <button id="noBtn">Não</button>
        </div>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const yesBtn = document.getElementById('yesBtn');

        // Faz o botão "Não" fugir ao ser clicado
        noBtn.addEventListener('click', (event) => {
            event.preventDefault();
            event.stopPropagation(); // Evita propagação de eventos
            const maxX = window.innerWidth - noBtn.offsetWidth - 20;
            const maxY = window.innerHeight - noBtn.offsetHeight - 20;
            const newX = Math.random() * maxX;
            const newY = Math.random() * maxY;
            noBtn.style.position = 'absolute';
            noBtn.style.left = `${newX}px`;
            noBtn.style.top = `${newY}px`;
        });

        // Faz o botão "Não" sumir e mostra o alerta ao clicar em "Sim"
        yesBtn.addEventListener('click', () => {
            noBtn.classList.add('hidden');
            alert('Aaaah, eu sabia! Te amo muito também! ♥');
        });
    </script>
</body>
</html>