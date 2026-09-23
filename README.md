<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>For Tình 💗</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #ffd6e7, #fff0f6);
            overflow: hidden;
        }

        .container {
            text-align: center;
            background: rgba(255,255,255,0.75);
            padding: 50px 35px;
            border-radius: 30px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.12);
            width: min(90%, 600px);
        }

        h1 {
            font-size: clamp(32px, 7vw, 60px);
            margin: 0 0 15px;
            color: #ff4f87;
        }

        p {
            font-size: 20px;
            color: #555;
            margin-bottom: 35px;
        }

        .buttons {
            position: relative;
            height: 100px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 25px;
        }

        button {
            border: none;
            padding: 15px 30px;
            border-radius: 999px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.2s;
        }

        #yes {
            background: #ff4f87;
            color: white;
            box-shadow: 0 8px 20px rgba(255,79,135,0.3);
        }

        #yes:hover {
            transform: scale(1.08);
        }

        #no {
            background: #eeeeee;
            color: #555;
            position: relative;
        }

        .heart {
            position: fixed;
            font-size: 24px;
            animation: float 4s linear forwards;
            pointer-events: none;
        }

        @keyframes float {
            0% {
                transform: translateY(0) scale(1);
                opacity: 1;
            }

            100% {
                transform: translateY(-100vh) scale(1.5);
                opacity: 0;
            }
        }

        #success {
            display: none;
        }

        #success h1 {
            font-size: clamp(40px, 9vw, 75px);
        }

        #success p {
            font-size: 24px;
        }
    </style>
</head>

<body>

    <!-- MÀN HÌNH CHÍNH -->
    <div class="container" id="main">
        <h1>Will you go out with me? 💗</h1>

        <p>I have a little question for you...</p>

        <div class="buttons">
            <button id="yes">YES 💕</button>
            <button id="no">NO</button>
        </div>
    </div>


    <!-- MÀN HÌNH SAU KHI BẤM YES -->
    <div class="container" id="success">
        <h1>YAYYYY 💗</h1>
        <p>
            I knew you would say yes 🥹💕
        </p>

        <div style="font-size: 60px;">
            🥰💗🌷✨
        </div>
    </div>


    <script>

        const noButton = document.getElementById("no");
        const yesButton = document.getElementById("yes");

        const messages = [
            "NO",
            "Think again",
            "Are you sure?",
            "Try again",
            "Choose the other one",
            "Really?",
            "Nope 😭",
            "You sure about that?",
            "Wrong button 😭",
            "Try YES 💗",
            "Pleaseee 🥺",
            "One more time",
            "Don't do this to me 😭"
        ];

        let messageIndex = 0;


        // ĐỔI CHỮ MỖI LẦN RÊ CHUỘT VÀO NO
        noButton.addEventListener("mouseenter", () => {

            messageIndex++;

            if (messageIndex >= messages.length) {
                messageIndex = 1;
            }

            noButton.textContent = messages[messageIndex];

            moveButton();
        });


        // DI CHUYỂN NÚT NO
        function moveButton() {

            const maxX = window.innerWidth - noButton.offsetWidth - 30;
            const maxY = window.innerHeight - noButton.offsetHeight - 30;

            const x = Math.max(20, Math.random() * maxX);
            const y = Math.max(20, Math.random() * maxY);

            noButton.style.position = "fixed";
            noButton.style.left = x + "px";
            noButton.style.top = y + "px";
        }


        // BẤM YES
        yesButton.addEventListener("click", () => {

            document.getElementById("main").style.display = "none";
            document.getElementById("success").style.display = "block";

            createHearts();
        });


        // TẠO TIM BAY
        function createHearts() {

            for (let i = 0; i < 35; i++) {

                setTimeout(() => {

                    const heart = document.createElement("div");

                    heart.className = "heart";
                    heart.textContent = ["💗", "💕", "💖", "💘", "❤️"][Math.floor(Math.random() * 5)];

                    heart.style.left = Math.random() * 100 + "vw";
                    heart.style.bottom = "-30px";
                    heart.style.animationDuration = (3 + Math.random() * 3) + "s";

                    document.body.appendChild(heart);

                    setTimeout(() => {
                        heart.remove();
                    }, 6000);

                }, i * 100);
            }
        }

    </script>

</body>
</html>
