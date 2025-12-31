<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Private Surprise for Nistha</title>
    <style>
        :root {
            --primary: #ff4d6d;
            --secondary: #c9184a;
            --glass: rgba(255, 255, 255, 0.9);
        }

        body, html {
            margin: 0;
            padding: 0;
            height: 100%;
            font-family: 'Segoe UI', sans-serif;
            background: linear-gradient(135deg, #fbc2eb 0%, #a6c1ee 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        /* Password Overlay */
        #lock-screen {
            position: fixed;
            inset: 0;
            background: white;
            z-index: 1000;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            transition: 0.8s ease-in-out;
        }

        .pass-box {
            text-align: center;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .hint {
            font-style: italic;
            color: #888;
            margin-bottom: 20px;
            font-size: 0.9em;
        }

        input[type="text"] {
            padding: 12px;
            border: 2px solid #eee;
            border-radius: 10px;
            width: 200px;
            font-size: 1.1em;
            outline: none;
            text-align: center;
            text-transform: uppercase;
        }

        /* Slide System */
        .container {
            width: 90%;
            max-width: 550px;
            height: 500px;
            position: relative;
        }

        .slide {
            position: absolute;
            inset: 0;
            background: var(--glass);
            backdrop-filter: blur(15px);
            padding: 40px;
            border-radius: 30px;
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            box-shadow: 0 20px 60px rgba(0,0,0,0.1);
            animation: flipIn 0.8s forwards;
        }

        .slide.active { display: flex; }

        @keyframes flipIn {
            from { opacity: 0; transform: rotateY(-20deg) translateY(30px); }
            to { opacity: 1; transform: rotateY(0) translateY(0); }
        }

        h1 { color: var(--primary); font-size: 2.2rem; margin-bottom: 10px; }
        p { color: #444; font-size: 1.1rem; line-height: 1.6; }

        .btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 14px 30px;
            border-radius: 50px;
            cursor: pointer;
            margin-top: 20px;
            transition: 0.3s;
        }

        .btn:hover { transform: scale(1.05); background: var(--secondary); }

        #nistha-img {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            border: 5px solid white;
            object-fit: cover;
            margin: 15px 0;
        }

        textarea { width: 100%; border-radius: 10px; padding: 10px; margin-top: 10px; border: 1px solid #ddd; }
        .heart { position: absolute; pointer-events: none; z-index: 50; }
    </style>
</head>
<body>

    <div id="lock-screen">
        <div class="pass-box">
            <h1>🔒 Private Surprise</h1>
            <p>Enter the secret code to unlock:</p>
            <p class="hint">💡 Hint: Old friends and old school</p>
            <input type="text" id="passInput" placeholder="Enter Code">
            <br>
            <button class="btn" onclick="checkPass()">Unlock Journey</button>
        </div>
    </div>

    <div class="container">
        <div class="slide" id="s1">
            <h1>Hi Nistha! ✨</h1>
            <p>Today is a very special day. I wanted to take you on a small trip down memory lane. Ready?</p>
            <button class="btn" onclick="next(2)">Let's Begin ➔</button>
        </div>

        <div class="slide" id="s2">
            <h1>Wishes for You 🌸</h1>
            <p>May your year be as bright as your smile and filled with endless positive moments.</p>
            <button class="btn" onclick="next(3)">Next ➔</button>
        </div>

        <div class="slide" id="s3">
            <h1>Happy Birthday! 🎉</h1>
            <img src="photo.jpg" alt="Nistha Jain" id="nistha-img">
            <p><strong>Nistha Jain</strong><br>Keep being the wonderful person you are!</p>
            <button class="btn" onclick="next(4)">Final Note ➔</button>
        </div>

        <div class="slide" id="s4">
            <h1>Reply Back 💌</h1>
            <p>I hope this brought a smile to your face! Leave a reply below.</p>
            <textarea id="reply" rows="3" placeholder="Type here..."></textarea>
            <button class="btn" onclick="submitReply()">Send Love 💖</button>
            <h2 id="finalMsg" style="display:none; color: var(--secondary);">Thank you! Have a wonderful day!</h2>
        </div>
    </div>

    <audio id="music"><source src="birthday.mp3" type="audio/mpeg"></audio>

    <script>
        function checkPass() {
            const input = document.getElementById('passInput').value.toUpperCase();
            if(input === "NPS") {
                document.getElementById('lock-screen').style.transform = "translateY(-100%)";
                document.getElementById('s1').classList.add('active');
                spawnHearts();
            } else {
                alert("Incorrect code! Remember the hint.");
            }
        }

        let current = 1;
        function next(n) {
            document.querySelectorAll('.slide').forEach(s => s.classList.remove('active'));
            document.getElementById('s' + n).classList.add('active');
            if(n === 2) document.getElementById('music').play().catch(() => {});
            spawnHearts();
        }

        function spawnHearts() {
            for(let i=0; i<30; i++) {
                const h = document.createElement('div');
                h.className = 'heart';
                h.innerHTML = ['❤️','💖','✨','🌸'][Math.floor(Math.random()*4)];
                h.style.left = Math.random() * 100 + 'vw';
                h.style.top = '100vh';
                h.style.fontSize = (Math.random() * 20 + 15) + 'px';
                document.body.appendChild(h);

                h.animate([
                    { transform: 'translateY(0)', opacity: 1 },
                    { transform: 'translateY(-110vh)', opacity: 0 }
                ], { duration: 3000 + Math.random() * 2000 }).onfinish = () => h.remove();
            }
        }

        function submitReply() {
            document.getElementById('reply').style.display = 'none';
            document.querySelector('#s4 .btn').style.display = 'none';
            document.getElementById('finalMsg').style.display = 'block';
            spawnHearts();
        }
    </script>
</body>
</html>
