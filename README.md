<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For Mayank ❤️</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: #ffe5ec;
            background: linear-gradient(135deg, #ffc2d1 0%, #ff85a1 100%);
            overflow: hidden;
            text-align: center;
        }

        .container {
            background: rgba(255, 255, 255, 0.95);
            padding: 40px 20px;
            border-radius: 30px;
            box-shadow: 0 15px 35px rgba(251, 111, 146, 0.4);
            border: 3px solid #fb6f92;
            width: 85%;
            max-width: 350px;
            z-index: 10;
            position: relative;
        }

        h1 {
            color: #ff477e;
            font-size: 1.6rem;
            margin-bottom: 10px;
        }

        .subtitle {
            color: #c9184a;
            font-size: 1.1rem;
            margin-bottom: 30px;
            font-weight: bold;
        }

        .buttons {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
        }

        button {
            padding: 15px 40px;
            font-size: 1.2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
            width: 80%;
        }

        #yesBtn {
            background-color: #ff477e;
            color: white;
            box-shadow: 0 5px 15px rgba(255, 71, 126, 0.4);
            z-index: 100;
        }

        #noBtn {
            background-color: #ffb3c1;
            color: #c9184a;
        }

        .heart-bg {
            position: absolute;
            font-size: 1.5rem;
            color: #ff477e;
            opacity: 0.6;
            z-index: 1;
            animation: float 5s infinite linear;
        }

        @keyframes float {
            0% { transform: translateY(110vh) rotate(0deg); }
            100% { transform: translateY(-10vh) rotate(360deg); }
        }

        .congrats-content {
            animation: pop 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        @keyframes pop {
            0% { transform: scale(0); }
            100% { transform: scale(1); }
        }
    </style>
</head>
<body>

    <div id="hearts-container"></div>

    <div class="container" id="card">
        <h1 id="title">Hey Mayank! ❤️</h1>
        <p class="subtitle" id="subTitle">Will you be my Valentine and my boyfriend?</p>
        <div class="buttons" id="btnGroup">
            <button id="yesBtn" onclick="celebrate()">Yes! 😍</button>
            <button id="noBtn" onclick="tryAgain()">No</button>
        </div>
    </div>

    <script>
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart-bg');
            heart.innerHTML = '💖';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
            heart.style.animationDuration = (Math.random() * 3 + 3) + 's';
            document.getElementById('hearts-container').appendChild(heart);
            setTimeout(() => heart.remove(), 6000);
        }
        setInterval(createHeart, 400);

        let attempt = 0;
        function tryAgain() {
            attempt++;
            const title = document.getElementById('title');
            const yesBtn = document.getElementById('yesBtn');
            const noBtn = document.getElementById('noBtn');
            
            title.innerText = "Try again, Mayank! 😉";
            
            // Make "Yes" button grow
            let scale = 1 + (attempt * 0.5);
            yesBtn.style.transform = `scale(${scale})`;
            
            // Move No button randomly
            const x = Math.random() * 40 - 20;
            const y = Math.random() * 40 - 20;
            noBtn.style.transform = `translate(${x}px, ${y}px)`;
        }

        function celebrate() {
            document.getElementById('card').innerHTML = `
                <div class="congrats-content">
                    <h1 style="font-size: 2rem;">YESSSS! 🎉</h1>
                    <p style="font-size: 1.2rem; color: #c9184a;">Congratulations Mayank!<br>You officially have a girlfriend now.</p>
                    <h2 style="color: #ff477e; margin-top: 20px;">Lots of love, Sakshi ❤️</h2>
                    <div style="font-size: 3.5rem; margin-top: 15px;">💏✨🌹</div>
                </div>
            `;
            for(let i=0; i<40; i++) setTimeout(createHeart, i*50);
        }
    </script>
</body>
</html>
