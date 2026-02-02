<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Top Secret for Akash</title>
    <style>
        body {
            background-color: #FFD1DC;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            position: relative;
        }
        /* Hiding content until unlocked */
        #mainContent { display: none; flex-direction: column; align-items: center; }
        
        #pass-container { z-index: 10; text-align: center; background: white; padding: 30px; border-radius: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); }
        input { padding: 12px; border-radius: 8px; border: 2px solid #D23369; margin-bottom: 15px; width: 200px; text-align: center; font-size: 1rem; }
        
        h1 { color: #D23369; z-index: 2; margin: 10px; }
        .bear-img { width: 250px; border-radius: 20px; z-index: 2; margin-bottom: 20px; }
        .btn-container { display: flex; gap: 20px; margin-top: 20px; z-index: 2; }
        .btn { background-color: #D23369; color: white; padding: 15px 30px; border: none; border-radius: 10px; cursor: pointer; font-weight: bold; }
        #noButton { position: absolute; transition: 0.1s; }
        .heart { position: absolute; color: #ff69b4; font-size: 20px; animation: float 5s linear infinite; bottom: -50px; z-index: 1; }
        @keyframes float { 0% { transform: translateY(0); opacity: 1; } 100% { transform: translateY(-110vh); opacity: 0; } }
    </style>
</head>
<body>

    <div id="pass-container">
        <h1>🔒 Secret Date Required</h1>
        <p style="color: #D23369;">When did our story start? ☀️</p>
        <input type="text" id="passwordInput" placeholder="DDMMYYYY or Date Name">
        <br>
        <button class="btn" onclick="checkPassword()">Unlock My Heart</button>
    </div>

    <div id="mainContent">
        <h1>-You are my sunshine-</h1>
        <img src="bears.jpg" class="bear-img" alt="Bears">
        <h1>Akash, Will you be my Valentine? ❤️</h1>

        <div class="btn-container">
            <button class="btn" onclick="alert('I knew it! ❤️')">Yes</button>
            <button class="btn" id="noButton" onmouseover="moveButton()">No</button>
        </div>
    </div>

    <script>
        function checkPassword() {
            const userInput = document.getElementById('passwordInput').value.toLowerCase().replace(/\s+/g, '');
            
            // This checks for "8march2025" or "08032025" or "8thmarch2025"
            if (userInput.includes("8march2025") || userInput.includes("08032025") || userInput.includes("8thmarch2025")) {
                document.getElementById('pass-container').style.display = 'none';
                document.getElementById('mainContent').style.display = 'flex';
                setInterval(createHeart, 300);
            } else {
                alert("That's not the right date! Think harder, Golu-Molu. 😘");
            }
        }

        function moveButton() {
            const x = Math.random() * (window.innerWidth - 100);
            const y = Math.random() * (window.innerHeight - 100);
            const btn = document.getElementById('noButton');
            btn.style.left = x + 'px';
            btn.style.top = y + 'px';
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (Math.random() * 3 + 2) + 's';
            document.body.appendChild(heart);
            setTimeout(() => { heart.remove(); }, 5000);
        }
    </script>
</body>
</html>
