<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy 20th Birthday BABE!</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&family=Sacramento&display=swap" rel="stylesheet">
    <style>
        /* --- CSS STYLES --- */
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #fdfbfb 0%, #ebedee 100%);
            background-color: #ffdde1; /* Fallback */
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
            color: #444;
        }

        .container {
            background: rgba(255, 255, 255, 0.9);
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            text-align: center;
            max-width: 400px;
            width: 90%;
            position: relative;
            transition: transform 0.3s ease;
        }

        h1 {
            font-family: 'Sacramento', cursive;
            color: #ff6b6b;
            font-size: 3rem;
            margin: 0;
        }

        p {
            font-size: 1.1rem;
            margin-bottom: 20px;
        }

        input {
            padding: 10px;
            border-radius: 10px;
            border: 1px solid #ddd;
            width: 70%;
            margin-bottom: 15px;
            font-size: 1rem;
            text-align: center;
        }

        button {
            background: #ff6b6b;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 50px;
            font-size: 1rem;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            font-weight: 600;
        }

        button:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
        }

        .hidden {
            display: none;
        }

        /* Quiz Styles */
        .quiz-option {
            background: #f0f0f0;
            margin: 5px 0;
            padding: 10px;
            border-radius: 10px;
            cursor: pointer;
            transition: background 0.3s;
        }
        .quiz-option:hover { background: #ffe0e0; }

        /* Cake Styles */
        .cake-container {
            margin-top: 30px;
            position: relative;
            height: 150px;
            display: flex;
            justify-content: center;
            align-items: flex-end;
        }
        
        .cake {
            width: 150px;
            height: 60px;
            background: #ff9a9e;
            border-radius: 10px 10px 0 0;
            position: relative;
        }
        
        .cake:before {
            content: '';
            position: absolute;
            width: 100%;
            height: 20px;
            background: #fad0c4;
            top: -20px;
            border-radius: 10px 10px 0 0;
        }

        .candle {
            width: 10px;
            height: 40px;
            background: #fff;
            position: absolute;
            bottom: 60px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 5px;
        }

        .flame {
            width: 15px;
            height: 25px;
            background: orange;
            border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
            position: absolute;
            top: -25px;
            left: 50%;
            transform: translateX(-50%);
            animation: flicker 1s infinite alternate;
            cursor: pointer;
            box-shadow: 0 0 10px orange;
        }

        @keyframes flicker {
            0% { transform: translateX(-50%) scale(1); opacity: 1; }
            100% { transform: translateX(-50%) scale(0.9); opacity: 0.8; }
        }

        .off {
            display: none;
        }
        
        #message-area {
            color: #ff6b6b;
            font-weight: bold;
            min-height: 30px;
        }

    </style>
</head>
<body>
<audio id="bgMusic" loop>
    <source src="song.mp3" type="audio/mpeg">
</audio>
    <div class="container" id="screen1">
        <h1>Happy Birthday Ishuuuu❤️!</h1>
        <p>To enter your party, enter the magic password.<br>(Hint: It's <strong>ME</strong>)</p>
        <input type="password" id="passwordInput" placeholder="Enter password...">
        <br>
        <button onclick="checkPassword()">Unlock</button>
        <p id="errorMsg" style="color:red; font-size:0.8rem; display:none;">Wrong password! Try "mere pyare patidev"</p>
    </div>

    <div class="container hidden" id="screen2">
        <h2>Level 1: The Quiz</h2>
        <p>Where we first met?</p>
        <div class="quiz-option" onclick="wrongAnswer()">The Movies</div>
        <div class="quiz-option" onclick="correctAnswer()">Ice Cream Parlour</div> 
        <div class="quiz-option" onclick="wrongAnswer()">Dominos Pizza</div> 
    </div>

    <div class="container hidden" id="screen3">
        <h2>Level 2: 20 Reasons</h2>
        <p>Since you are 20, here is why I love you.</p>
        <div id="reason-display" style="font-style: italic; margin: 20px; color: #555;">Click the button...</div>
        <button onclick="generateReason()">Tell me why❤️</button>
        <br><br>
        <button onclick="nextLevel()" style="background: #444; font-size: 0.8rem;">Go to Cake</button>
    </div>

    <div class="container hidden" id="screen4">
        <h1>Make a Wish!</h1>
        <p>Click the flame to blow out the candle.</p>
        
        <div class="cake-container">
            <div class="cake">
                <div class="candle">
                    <div class="flame" id="flame" onclick="blowCandle()"></div>
                </div>
            </div>
        </div>
    </div>

    <div class="container hidden" id="screen5">
        <h1>Happy 20th Sweetie!</h1>
        <p>Welcome to your 20s, my love. I hope this decade is as beautiful as you are, and all the wishes of yours becomes true god bless this crazy girl always because you are the most precious thing for me always be the same and thankyou for keeping up with my tantrums i wish we have this never ending journey forever my love and treat me with good food okay and just saying i love your cooking and singing soo much as i am an girlfriend addict eehhhee, as i know your perfect in everything you pawfect in dancing you pawfect in singing you pawfect at riding bike just as you ride m... uuhhuu, i know sometimes things had been hard between us but i promise the only thing will be hard between us is mahh dihh..uhhhuuu because you makes me loose control argghhh, anyways happy birthday sweetiepatootiee lods of kisses for you from your love❤️.</p>
        <p>I love you❤️</p>
        
        <br>
        <button onclick="restart()">Replay</button>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <script>
        // --- JAVASCRIPT LOGIC ---

        // 1. PASSWORD CHECK
        function checkPassword() {
    const pass = document.getElementById('passwordInput').value.toLowerCase();
    
    // CHANGE "mere pyare patidev" to your password
    if (pass === "mere pyare patidev") {
        // This line starts the music!
        document.getElementById('bgMusic').play();
        
        switchScreen('screen1', 'screen2');
    } else {
        document.getElementById('errorMsg').style.display = 'block';
    }
}
        // 2. QUIZ LOGIC
        function wrongAnswer() {
            alert("Nope! Try again 😜");
        }

        function correctAnswer() {
            alert("Correct! You know us so well 😘");
            switchScreen('screen2', 'screen3');
        }

        // 3. REASONS GENERATOR
        // EDIT THESE REASONS WITH YOUR OWN
        const reasons = [
            "Your smile lights up my world.",
            "You make the best Maggie.",
            "Your laugh is my favorite sound.",
            "You support my dreams.",
            "You are beautiful inside and out iykyk.",
            "The way you look at me makes me shy.",
            "You are stronger than you know.",
            "Your kindness to others.",
            "Our late night talks.",
            "You have the cutest nose.",
            "You're my best friend.",
            "How hard you work.",
            "Your warm hugs.",
            "You understand me like no one else.",
            "You'r cute moustache.",
            "You make boring things fun.",
            "Your style is amazing.",
            "You handle my bad jokes.",
            "I can be myself around you.",
            "I simply love you."
        ];

        function generateReason() {
            const randomReason = reasons[Math.floor(Math.random() * reasons.length)];
            document.getElementById('reason-display').innerText = randomReason;
        }

        function nextLevel() {
            switchScreen('screen3', 'screen4');
        }

        // 4. CANDLE BLOW OUT
        function blowCandle() {
            document.getElementById('flame').classList.add('off');
            document.querySelector('h1').innerText = "Yay!";
            document.querySelector('p').innerText = "Wish Granted ✨";
            
            // Trigger Confetti
            confetti({
                particleCount: 150,
                spread: 70,
                origin: { y: 0.6 }
            });

            setTimeout(() => {
                switchScreen('screen4', 'screen5');
                launchBigConfetti();
            }, 2000);
        }

        function launchBigConfetti() {
            var duration = 3000;
            var animationEnd = Date.now() + duration;
            var defaults = { startVelocity: 30, spread: 360, ticks: 60, zIndex: 0 };

            var interval = setInterval(function() {
                var timeLeft = animationEnd - Date.now();

                if (timeLeft <= 0) {
                    return clearInterval(interval);
                }

                var particleCount = 50 * (timeLeft / duration);
                confetti(Object.assign({}, defaults, { particleCount, origin: { x: Math.random(), y: Math.random() - 0.2 } }));
            }, 250);
        }

        // HELPER FUNCTION
        function switchScreen(fromId, toId) {
            document.getElementById(fromId).classList.add('hidden');
            document.getElementById(toId).classList.remove('hidden');
        }

        function restart() {
            location.reload();
        }
    </script>
</body>
</html>
