<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Magical Journey for Nistha</title>
    <style>
        :root {
            --primary: #ff4d6d;
            --secondary: #c9184a;
            --accent: #ffb703;
            --glass: rgba(255, 255, 255, 0.8);
        }

        /* Animated Aurora Background */
        body {
            margin: 0; padding: 0; height: 100vh;
            font-family: 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
            display: flex; align-items: center; justify-content: center;
            overflow: hidden;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Lock Screen */
        #lock-screen {
            position: fixed; inset: 0; background: rgba(255,255,255,0.95); z-index: 1000;
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            transition: transform 1.2s cubic-bezier(1, 0, 0, 1);
        }

        .pass-box { 
            background: white; padding: 50px; border-radius: 30px; 
            box-shadow: 0 20px 60px rgba(0,0,0,0.1); text-align: center;
        }

        input[type="text"] {
            padding: 15px; border: 2px solid var(--primary); border-radius: 12px;
            width: 220px; font-size: 1.2em; outline: none; text-align: center;
            text-transform: uppercase; letter-spacing: 3px;
        }

        /* Main Container */
        .container { width: 90%; max-width: 500px; height: 550px; position: relative; }

        .slide {
            position: absolute; inset: 0; background: var(--glass);
            backdrop-filter: blur(20px); padding: 40px; border-radius: 40px;
            display: none; flex-direction: column; align-items: center; justify-content: center;
            text-align: center; box-shadow: 0 30px 60px rgba(0,0,0,0.2);
            border: 1px solid rgba(255,255,255,0.5);
            animation: slideReveal 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        .slide.active { display: flex; }

        @keyframes slideReveal {
            from { opacity: 0; transform: scale(0.8) translateY(50px); }
            to { opacity: 1; transform: scale(1) translateY(0); }
        }

        h1 { color: var(--secondary); font-size: 2.5rem; margin-bottom: 10px; font-weight: 800; }
        p { color: #333; font-size: 1.2rem; line-height: 1.6; }

        .btn {
            background: var(--primary); color: white; border: none;
            padding: 16px 40px; border-radius: 50px; cursor: pointer;
            margin-top: 25px; font-weight: bold; font-size: 1.1rem;
            transition: 0.4s; box-shadow: 0 10px 20px rgba(255, 77, 109, 0.4);
        }

        .btn:hover { transform: translateY(-5px) scale(1.05); background: var(--secondary); }

        #nistha-img { 
            width: 200px; height: 200px; border-radius: 30px; 
            border: 6px solid white; object-fit: cover; margin: 20px 0;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        textarea { 
            width: 100%; border-radius: 15px; padding: 15px; 
            margin-top: 20px; border: 2px solid #ffccd5; 
            font-family: inherit; font-size: 1rem;
        }

        .particle { position: absolute; pointer-events: none; z-index: 50; }
    </style>
</head>
<body>

    <div id="lock-screen">
        <div class="pass-box">
            <h1 style="color: #444;">✨ A Secret Surprise</h1>
            [span_0](start_span)[span_1](start_span)<p style="color: #888; font-style: italic; margin-bottom: 25px;">Hint: Old friends and old school[span_0](end_span)[span_1](end_span)</p>
            <input type="text" id="passInput" placeholder="ENTER CODE">
            <br>
            <button class="btn" onclick="checkPass()">Unlock Magic</button>
        </div>
    </div>

    <div class="container">
        <div class="slide" id="s1">
            <h1>Hi Nistha! 💖</h1>
            <p>I built this small digital world to celebrate you. Ready to explore?</p>
            <button class="btn" onclick="next(2)">Let's Go! ➔</button>
        </div>

        <div class="slide" id="s2">
            <h1>Heartfelt Wish 🌸</h1>
            [span_2](start_span)[span_3](start_span)<p>May your year be as beautiful as your soul and as bright as your smile.[span_2](end_span)[span_3](end_span)</p>
            <button class="btn" onclick="next(3)">Continue ➔</button>
        </div>

        <div class="slide" id="s3">
            <h1>Happy Birthday! 🎈</h1>
            [span_4](start_span)[span_5](start_span)<img src="photo.jpg" alt="Nistha" id="nistha-img"> <p><strong>Nistha Jain</strong><br>You are a wonderful person—stay happy and keep shining[span_4](end_span)[span_5](end_span)!</p>
            <button class="btn" onclick="next(4)">One Last Thing ➔</button>
        </div>

        <div class="slide" id="s4">
            <h1>Send Love Back 💌</h1>
            [span_6](start_span)<p>If this made you smile, leave a small message here for me.[span_6](end_span)</p>
            <textarea id="reply" rows="3" placeholder="Write your heart out..."></textarea>
            <button class="btn" onclick="submitReply()">Send Message ➔</button>
            <h2 id="finalMsg" style="display:none; color: var(--secondary);">Message Received! ❤️</h2>
        </div>
    </div>

    <audio id="music"><source src="birthday.mp3" type="audio/mpeg"></audio>

    <script>
        function checkPass() {
            const input = document.getElementById('passInput').value.toUpperCase();
            [span_7](start_span)if(input === "NPS") { //[span_7](end_span)
                document.getElementById('lock-screen').style.transform = "translateY(-100%)";
                document.getElementById('s1').classList.add('active');
                spawnParticles();
            } else { alert("Incorrect code! Try again."); }
        }

        function next(n) {
            document.querySelectorAll('.slide').forEach(s => s.classList.remove('active'));
            document.getElementById('s' + n).classList.add('active');
            if(n === 2) {
                document.getElementById('music').play().catch(() => {});
            }
            spawnParticles();
        }

        function spawnParticles() {
            for(let i=0; i<40; i++) {
                const p = document.createElement('div');
                p.className = 'particle';
                p.innerHTML = ['❤️','💖','✨','⭐','🌸'][Math.floor(Math.random()*5)];
                p.style.left = Math.random() * 100 + 'vw';
                p.style.top = '100vh';
                p.style.fontSize = (Math.random() * 25 + 15) + 'px';
                document.body.appendChild(p);

                p.animate([
                    { transform: 'translateY(0) rotate(0deg)', opacity: 1 },
                    { transform: `translateY(-110vh) rotate(${Math.random() * 720}deg)`, opacity: 0 }
                ], {
                    duration: 3000 + Math.random() * 2000,
                    easing: 'ease-out'
                }).onfinish = () => p.remove();
            }
        }

        function submitReply() {
            document.getElementById('reply').style.display = 'none';
            document.querySelector('#s4 .btn').style.display = 'none';
            document.getElementById('finalMsg').style.display = 'block';
            for(let i=0; i<3; i++) setTimeout(spawnParticles, i * 400);
        }
    </script>
</body>
</html>

