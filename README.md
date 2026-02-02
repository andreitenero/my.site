# my.site
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Ultra Fun and Funny Valentine's Proposal for Teya</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: linear-gradient(to bottom, #ff69b4, #ffb6c1);
            color: white;
            padding: 20px;
            overflow: hidden;
        }
        .screen {
            display: none;
        }
        .active {
            display: block;
            animation: fadeIn 1s, rainbow 2s infinite;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes rainbow {
            0% { background: linear-gradient(to bottom, #ff69b4, #ffb6c1); }
            50% { background: linear-gradient(to bottom, #ff1493, #00ffff); }
            100% { background: linear-gradient(to bottom, #ff69b4, #ffb6c1); }
        }
        button {
            padding: 10px 20px;
            font-size: 18px;
            margin: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s;
        }
        .yes {
            background: #4CAF50;
            color: white;
        }
        .no {
            background: #f44336;
            color: white;
            position: absolute;
        }
        .choice {
            background: #2196F3;
            color: white;
        }
        .hearts {
            position: absolute;
            font-size: 40px;
            animation: float 3s infinite, dance 1s infinite;
            pointer-events: none;
            cursor: grab;
        }
        @keyframes float {
            0% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
            100% { transform: translateY(0); }
        }
        @keyframes dance {
            0% { transform: rotate(0deg); }
            25% { transform: rotate(5deg); }
            50% { transform: rotate(-5deg); }
            75% { transform: rotate(5deg); }
            100% { transform: rotate(0deg); }
        }
        .confetti {
            position: absolute;
            font-size: 20px;
            animation: explode 1s forwards;
        }
        @keyframes explode {
            0% { opacity: 1; transform: scale(1); }
            100% { opacity: 0; transform: scale(2) translateY(-50px); }
        }
        #countdown {
            font-size: 24px;
            color: yellow;
        }
        #poem {
            font-size: 18px;
            margin: 20px;
            line-height: 1.5;
        }
        .maze {
            position: relative;
            width: 300px;
            height: 200px;
            margin: 20px auto;
            border: 2px solid white;
        }
        .maze-btn {
            position: absolute;
            width: 50px;
            height: 50px;
            background: pink;
            border-radius: 50%;
        }
        .drag-heart {
            cursor: grab;
        }
    </style>
</head>
<body>
    <div id="screen1" class="screen active">
        <h1>Teya, Will You Be My Valentine?</h1>
        <p>Choose wisely... or watch it explode! 😉</p>
        <button class="yes" onclick="explode(this); nextScreen(2)">Yes!</button>
        <button class="no" onmouseover="dodge()" onclick="tease()">No</button>
    </div>
    <div id="screen2" class="screen">
        <h2>Funny Quiz for Teya: What's My Favorite Thing About You?</h2>
        <button class="choice" onclick="quizAnswer('Your smile—punderful!')">Your Smile</button>
        <button class="choice" onclick="quizAnswer('Your laugh—hilarious!')">Your Laugh</button>
        <button class="choice" onclick="quizAnswer('Everything—total win!')">Everything!</button>
    </div>
    <div id="screen3" class="screen">
        <h2>Teya, You Got It Right! But Let's Play a Game...</h2>
        <p>Catch the 'No' if you can! Countdown: <span id="countdown">5</span></p>
        <button class="yes" onclick="explode(this); nextScreen(4)">Yes, I'm Ready!</button>
        <button class="no" onmouseover="dodge()" onclick="tease()">No</button>
    </div>
    <div id="screen4" class="screen">
        <h2>Funny Compliments for Teya</h2>
        <div id="compliments">You're so sweet, you make candy jealous! 🍬</div>
        <button class="yes" onclick="explode(this); nextScreen(5)">Haha, Thanks!</button>
    </div>
    <div id="screen5" class="screen">
        <h2>Teya, Pick a Silly Superpower!</h2>
        <button class="choice" onclick="powerPick('Flying')">Flying (Like a lovebird!)</button>
        <button class="choice" onclick="powerPick('Invisibility')">Invisibility (But I'd still see your heart!)</button>
        <button class="choice" onclick="powerPick('Time Travel')">Time Travel (To relive our dates!)</button>
    </div>
    <div id="screen6" class="screen">
        <h2>A Punny Love Poem for Teya</h2>
        <div id="poem">Roses are red, violets are blue,<br>Teya, you're 'punderful,' and I love you!<br>Your smile's so bright, it could light the moon,<br>Will you be mine? Let's spoon! 🥄</div>
        <button class="yes" onclick="explode(this); nextScreen(7)">That's Punny!</button>
    </div>
    <div id="screen7" class="screen">
        <h2>Teya, Escape the Maze? (Spoiler: It's a Joke!)</h2>
        <p>Click the pink dots—BOING! They teleport!</p>
        <div class="maze">
            <button class="maze-btn" style="top: 20px; left: 20px;" onclick="mazeFail()"></button>
            <button class="maze-btn" style="top: 100px; left: 150px;" onclick="mazeFail()"></button>
        </div>
        <button class="yes" onclick="explode(this); nextScreen(8)">I Give Up—Yes!</button>
    </div>
    <div id="screen8" class="screen">
        <h2>Drag the Hearts, Teya! Catch the Love!</h2>
        <div class="hearts drag-heart" draggable="true" ondragstart="dragStart(event)" ondragend="dragEnd(event)">❤️</div>
        <div class="hearts drag-heart" draggable="true" ondragstart="dragStart(event)" ondragend="dragEnd(event)">💕</div>
        <button class="yes" onclick="explode(this); nextScreen(9)">Caught 'Em!</button>
    </div>
    <div id="screen9" class="screen">
        <h2>Light Roast for Teya (But I Love You Anyway!)</h2>
        <div id="roast">You're so cute, you make puppies look ugly! 🐶</div>
        <button class="yes" onclick="explode(this); nextScreen(10)">Ouch, But Yes!</button>
    </div>
    <div id="screen10" class="screen">
        <h1>Happy Valentine's Day, Teya! 💖</h1>
        <p>You make my heart skip a beat. I love you endlessly—yes, forever! Let's keep the laughs coming. 😘</p>
        <div class="hearts">❤️</div>
        <div class="hearts" style="left: 50%;">💕</div>
        <div class="hearts" style="left: 70%;">😘</div>
        <div class="hearts" style="left: 20%;">🌹</div>
        <div class="hearts" style="left: 80%;">💑</div>
    </div>

    <script>
        let currentScreen = 1;
        let complimentIndex = 0;
        let roastIndex = 0;
        const compliments = ["You're so sweet, you make candy jealous! 🍬", "Your laugh is contagious—like a virus, but cute! 😂", "Teya, you're my favorite adventure—full of twists! 🗺️", "I love your kind heart—it beats mine! ❤️"];
        const roasts = ["You're so cute, you make puppies look ugly! 🐶", "Teya, you're so funny, you crack me up—literally! 😆", "You're my sunshine, but with more sass! ☀️"];

        function nextScreen(num) {
            document.getElementById('screen' + currentScreen).classList.remove('active');
            currentScreen = num;
            document.getElementById('screen' + currentScreen).classList.add('active');
            if (num === 3) startCountdown();
            if (num === 4) startCompliments();
            if (num === 6) startPoem();
            if (num === 9) startRoast();
        }

        function quizAnswer(answer) {
            alert(`Teya, ${answer} You always make me grin! 😊`);
            nextScreen(3);
        }

        function powerPick(power) {
            alert(`Teya, ${power} is awesome—and it matches how amazing you are! ❤️`);
            nextScreen(6);
        }

        function mazeFail() {
            alert("BOING! Teya, you 'escaped'... right into a hug! Yes! 😘");
            nextScreen(8);
        }

        function explode(btn) {
            const confetti = document.createElement('div');
            confetti.className = 'confetti';
            confetti.textContent = '🎉';
            confetti.style.left = btn.offsetLeft + 'px';
            confetti.style.top = btn.offsetTop + 'px';
            document.body.appendChild(confetti);
            setTimeout(() => confetti.remove(), 1000);
        }

        function dodge() {
            const noBtn = document.querySelector('.no');
            noBtn.style.left = Math.random() * (window.innerWidth - 100) + 'px';
            noBtn.style.top = Math.random() * (window.innerHeight - 100) + 'px';
        }

        function tease() {
            alert("Teya, nope! That button just did the cha-cha away! 😏");
            nextScreen(currentScreen === 1 ? 2 : 7);
        }

        function startCountdown() {
            let count = 5;
            const timer = setInterval(() => {
                document.getElementById('countdown').textContent = count;
                count--;
                if (count < 0) {
                    clearInterval(timer);
                    nextScreen(4);
                }
            }, 1000);
        }

        function startCompliments() {
            const compEl = document.getElementById('compliments');
            setInterval(() => {
                complimentIndex = (complimentIndex + 1) % compliments.length;
                compEl.textContent = compliments[complimentIndex];
            }, 2000);
        }

        function startPoem() {
            setTimeout(() => nextScreen(7), 8000);
        }

        function startRoast() {
            const roastEl = document.getElementById('roast');
            setInterval(() => {
                roastIndex = (roastIndex + 1) % roasts.length;
                roastEl.textContent = roasts[roastIndex];
            }, 2000);
        }

        function dragStart(e) {
            e.dataTransfer.setData('text', e.target.textContent);
        }

        function dragEnd(e) {
            alert("Teya, you caught the love! Yes! 💕");
        }
    </script>
</body>
</html>
