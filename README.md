<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Message for Mayank</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: #ffdae0;
            background: linear-gradient(180deg, #ffdae0 0%, #ffb3c1 100%);
            overflow: hidden;
            text-align: center;
        }

        .container {
            background: white;
            padding: 40px 20px;
            border-radius: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            width: 85%;
            max-width: 380px;
            position: relative;
            z-index: 10;
        }

        h1 {
            color: #d63384;
            font-size: 1.5rem;
            margin-bottom: 25px;
            line-height: 1.4;
        }

        .buttons {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
        }

        button {
            padding: 15px 30px;
            font-size: 1.1rem;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            font-weight: bold;
            transition: transform 0.2s;
            width: 80%;
        }

        #yesBtn {
            background-color: #ff4d6d;
            color: white;
        }

        #noBtn {
            background-color: #f8f9fa;
            color: #6c757d;
            border: 1px solid #dee2e6;
        }

        .heart {
            position: absolute;
            color: #ff4d6d;
            font-size: 1.5rem;
            animation: floatUp 4s infinite linear;
            opacity: 0.7;
        }

        @keyframes floatUp {
            0% { transform: translateY(100vh); opacity: 1; }
            100% { transform: translateY(-10vh); opacity: 0; }
        }
    </style>
</head>
<body>

    <div id="hearts-container"></div>

    <div class="container" id="content">
        <!-- THE QUESTION SECTION -->
        <h1 id="question">Mayank, you wanted a label, right?<br><br>So... Will you be my boyfriend?</h1>
        
        <div class="buttons">
            <button id="yesBtn" onclick="onYes()">Yes! 😍</button>
            <button id="noBtn" onclick="onNo()">No 🤨</button>
        </div>
    </div>

    <script>
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
            document.getElementById('hearts-container').appendChild(heart);
            setTimeout(() => heart.remove(), 4000);
        }
        setInterval(createHeart, 400);

        let clickCount = 0;

        function onNo() {
            clickCount++;
            const question = document.getElementById('question');
            const yesBtn = document.getElementById('yesBtn');
            
            // Funny "No" responses
            if(clickCount == 1) question.innerText = "Try again, Mayank! 😉";
            if(clickCount == 2) question.innerText = "Are you sure? Think again... 🙄";
            if(clickCount >= 3) question.innerText = "Wrong button! The 'Yes' button is right there. 👉";
            
            let newSize = 1 + (clickCount * 0.4);
            yesBtn.style.transform = `scale(${newSize})`;
            
            const noBtn = document.getElementById('noBtn');
            noBtn.style.transform = `translate(${Math.random() * 30 - 15}px, ${Math.random() * 30 - 15}px)`;
        }

        function onYes() {
            document.getElementById('content').innerHTML = `
                <div style="animation: fadeIn 0.8s ease-in;">
                    <h1 style="color: #ff4d6d;">Congratulations! 🎉</h1>
                    <p style="font-size: 1.2rem; color: #333; line-height: 1.5;">
                        Now you have someone to annoy you! Hehe ❤️
                    </p>
                    <h2 style="color: #d63384; margin-top: 20px;">- Sakshi</h2>
                </div>
            `;
            for(let i=0; i<30; i++) setTimeout(createHeart, i*100);
        }
    </script>
</body>
</html>
