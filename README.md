<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cartoon Fun World</title>
    <style>
        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            background-color: #87CEEB;
            margin: 0;
            padding: 0;
            overflow-x: hidden;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        h1 {
            color: #FF6347;
            text-align: center;
            font-size: 3em;
            text-shadow: 2px 2px #FFA500;
        }
        .character {
            width: 100px;
            height: 100px;
            background-size: cover;
            position: absolute;
            cursor: pointer;
            transition: transform 0.3s;
        }
        #char1 {
            background-image: url('https://via.placeholder.com/100x100.png?text=Char1');
            top: 50px;
            left: 50px;
            animation: bounce 2s infinite;
        }
        #char2 {
            background-image: url('https://via.placeholder.com/100x100.png?text=Char2');
            top: 200px;
            right: 50px;
            animation: rotate 3s infinite linear;
        }
        #char3 {
            background-image: url('https://via.placeholder.com/100x100.png?text=Char3');
            bottom: 50px;
            left: 50%;
            animation: shake 0.82s cubic-bezier(.36,.07,.19,.97) infinite;
        }
        .character:hover {
            transform: scale(1.2);
        }
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        @keyframes shake {
            10%, 90% { transform: translate3d(-1px, 0, 0); }
            20%, 80% { transform: translate3d(2px, 0, 0); }
            30%, 50%, 70% { transform: translate3d(-4px, 0, 0); }
            40%, 60% { transform: translate3d(4px, 0, 0); }
        }
        .sun {
            width: 100px;
            height: 100px;
            background: yellow;
            border-radius: 50%;
            position: absolute;
            top: 20px;
            right: 20px;
            box-shadow: 0 0 20px yellow;
            animation: pulse 2s infinite;
        }
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        .cloud {
            background: white;
            border-radius: 50px;
            width: 200px;
            height: 60px;
            position: absolute;
            top: 100px;
            left: -200px;
            animation: moveCloud 15s infinite linear;
        }
        .cloud:before, .cloud:after {
            content: '';
            background: white;
            border-radius: 50%;
            position: absolute;
        }
        .cloud:before {
            width: 100px;
            height: 100px;
            top: -50px;
            left: 10px;
        }
        .cloud:after {
            width: 120px;
            height: 120px;
            top: -70px;
            right: 10px;
        }
        @keyframes moveCloud {
            from { left: -200px; }
            to { left: 100%; }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Welcome to Cartoon Fun World!</h1>
        <p>Click on the characters to see what happens!</p>
    </div>
    <div id="char1" class="character"></div>
    <div id="char2" class="character"></div>
    <div id="char3" class="character"></div>
    <div class="sun"></div>
    <div class="cloud"></div>

    <script>
        document.querySelectorAll('.character').forEach(char => {
            char.addEventListener('click', () => {
                const sounds = ['Boing!', 'Zoom!', 'Pow!', 'Whoosh!', 'Zap!'];
                const randomSound = sounds[Math.floor(Math.random() * sounds.length)];
                alert(randomSound);
            });
        });

        function moveCharacter(charId) {
            const char = document.getElementById(charId);
            const maxX = window.innerWidth - char.offsetWidth;
            const maxY = window.innerHeight - char.offsetHeight;
            const newX = Math.random() * maxX;
            const newY = Math.random() * maxY;
            char.style.left = `${newX}px`;
            char.style.top = `${newY}px`;
        }

        setInterval(() => moveCharacter('char3'), 3000);
    </script>
</body>
</html>
