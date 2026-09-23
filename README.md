<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>A Little Question 💗</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-height: 100vh;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #ffd6e7, #fff4f8);
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    color: #444;
}

.card {
    width: min(92%, 600px);
    background: rgba(255,255,255,0.9);
    padding: 40px 28px;
    border-radius: 30px;
    text-align: center;
    box-shadow: 0 15px 45px rgba(0,0,0,0.12);
    animation: appear 0.7s ease;
}

@keyframes appear {
    from {
        opacity: 0;
        transform: translateY(20px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

h1 {
    color: #ff4f87;
    font-size: clamp(32px, 7vw, 55px);
    margin: 0 0 15px;
}

.subtitle {
    font-size: 19px;
    margin-bottom: 35px;
    color: #666;
}

.buttons {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
    min-height: 80px;
}

button {
    border: none;
    border-radius: 999px;
    padding: 15px 28px;
    font-size: 17px;
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
    background: #eee;
    color: #555;
    position: relative;
}

/* FORM */

#datePage {
    display: none;
}

.form-title {
    color: #ff4f87;
    font-size: 38px;
    margin-bottom: 10px;
}

.form-subtitle {
    color: #777;
    margin-bottom: 25px;
}

.form-group {
    text-align: left;
    margin-bottom: 18px;
}

label {
    display: block;
    font-weight: bold;
    margin-bottom: 7px;
    color: #555;
}

input {
    width: 100%;
    padding: 14px 15px;
    border: 2px solid #ffd0df;
    border-radius: 15px;
    font-size: 16px;
    outline: none;
    background: white;
}

input:focus {
    border-color: #ff6f9d;
}

#confirm {
    width: 100%;
    background: #ff4f87;
    color: white;
    margin-top: 10px;
}

#confirm:hover {
    transform: scale(1.02);
}

/* SUCCESS */

#successPage {
    display: none;
}

.success-title {
    color: #ff4f87;
    font-size: 45px;
    margin-bottom: 10px;
}

.date-box {
    background: #fff0f5;
    border-radius: 20px;
    padding: 20px;
    margin: 25px 0;
    text-align: left;
}

.date-box div {
    margin: 12px 0;
    font-size: 18px;
}

.heart {
    position: fixed;
    bottom: -30px;
    font-size: 25px;
    pointer-events: none;
    animation: floatUp 4s linear forwards;
}

@keyframes floatUp {
    0% {
        transform: translateY(0) scale(1);
        opacity: 1;
    }

    100% {
        transform: translateY(-110vh) scale(1.5);
        opacity: 0;
    }
}

.small {
    font-size: 14px;
    color: #999;
    margin-top: 20px;
}
</style>
</head>


<body>

<!-- =========================
     TRANG 1
========================= -->

<div class="card" id="questionPage">

    <h1>Will you go out with me? 💗</h1>

    <div class="subtitle">
        I have a little question for you...
    </div>

    <div class="buttons">

        <button id="yes">
            YES 💕
        </button>

        <button id="no">
            NO
        </button>

    </div>

</div>


<!-- =========================
     TRANG 2 - CHỌN NGÀY
========================= -->

<div class="card" id="datePage">

    <div class="form-title">
        YAYYYY 💗
    </div>

    <div class="form-subtitle">
        Then let's plan our date 🥹
    </div>


    <div class="form-group">

        <label for="date">
            📅 When?
        </label>

        <input
            type="date"
            id="date"
        >

    </div>


    <div class="form-group">

        <label for="time">
            ⏰ What time?
        </label>

        <input
            type="time"
            id="time"
        >

    </div>


    <div class="form-group">

        <label for="place">
            📍 Where?
        </label>

        <input
            type="text"
            id="place"
            placeholder="Enter a place..."
        >

    </div>


    <button id="confirm">
        Confirm our date 💕
    </button>

</div>


<!-- =========================
     TRANG 3 - HOÀN TẤT
========================= -->

<div class="card" id="successPage">

    <div class="success-title">
        It's a date! 🥹💕
    </div>

    <div>
        I can't wait to see you ✨
    </div>


    <div class="date-box">

        <div>
            📅 <strong>Date:</strong>
            <span id="showDate"></span>
        </div>

        <div>
            ⏰ <strong>Time:</strong>
            <span id="showTime"></span>
        </div>

        <div>
            📍 <strong>Place:</strong>
            <span id="showPlace"></span>
        </div>

    </div>


    <div style="font-size:55px;">
        💗🌷✨🥰
    </div>

    <div class="small">
        See you on our date 💕
    </div>

</div>


<script>

/* =========================
   NO BUTTON
========================= */

const noButton = document.getElementById("no");

const messages = [
    "NO",
    "Think again",
    "Are you sure?",
    "Try again",
    "Choose the other one",
    "Really?",
    "Wrong button 😭",
    "You sure?",
    "Try YES 💗",
    "Pleaseee 🥺",
    "One more time",
    "Don't do this to me 😭",
    "NOPE 😂",
    "You can't catch me"
];

let messageIndex = 0;


function moveNoButton() {

    messageIndex++;

    if (messageIndex >= messages.length) {
        messageIndex = 1;
    }

    noButton.innerText = messages[messageIndex];


    const maxX =
        window.innerWidth - noButton.offsetWidth - 20;

    const maxY =
        window.innerHeight - noButton.offsetHeight - 20;


    const randomX =
        Math.max(10, Math.random() * maxX);

    const randomY =
        Math.max(10, Math.random() * maxY);


    noButton.style.position = "fixed";

    noButton.style.left = randomX + "px";

    noButton.style.top = randomY + "px";
}


/* Máy tính */

noButton.addEventListener(
    "mouseenter",
    moveNoButton
);


/* Điện thoại */

noButton.addEventListener(
    "touchstart",
    function(event) {

        event.preventDefault();

        moveNoButton();

    }
);


/* =========================
   YES
========================= */

const yesButton =
    document.getElementById("yes");

const questionPage =
    document.getElementById("questionPage");

const datePage =
    document.getElementById("datePage");


yesButton.addEventListener(
    "click",
    function() {

        questionPage.style.display = "none";

        datePage.style.display = "block";

    }
);


/* =========================
   CHỌN NGÀY
========================= */

const dateInput =
    document.getElementById("date");


/* Không cho chọn ngày trong quá khứ */

const today =
    new Date().toISOString().split("T")[0];

dateInput.min = today;


/* =========================
   CONFIRM
========================= */

const confirmButton =
    document.getElementById("confirm");


confirmButton.addEventListener(
    "click",
    function() {

        const selectedDate =
            document.getElementById("date").value;

        const selectedTime =
            document.getElementById("time").value;

        const selectedPlace =
            document.getElementById("place").value.trim();


        if (!selectedDate) {

            alert("Choose a date first 💗");

            return;
        }


        if (!selectedTime) {

            alert("Choose a time first ⏰");

            return;
        }


        if (!selectedPlace) {

            alert("Where should we go? 📍");

            return;
        }


        /* Đổi format ngày */

        const dateObject =
            new Date(selectedDate + "T00:00:00");


        const formattedDate =
            dateObject.toLocaleDateString(
                "en-US",
                {
                    weekday: "long",
                    year: "numeric",
                    month: "long",
                    day: "numeric"
                }
            );


        document.getElementById("showDate")
            .innerText = formattedDate;


        document.getElementById("showTime")
            .innerText = selectedTime;


        document.getElementById("showPlace")
            .innerText = selectedPlace;


        datePage.style.display = "none";

        document.getElementById("successPage")
            .style.display = "block";


        createHearts();

    }
);


/* =========================
   TIM BAY
========================= */

function createHearts() {

    for (let i = 0; i < 40; i++) {

        setTimeout(function() {

            const heart =
                document.createElement("div");


            heart.className = "heart";


            const hearts = [
                "💗",
                "💕",
                "💖",
                "❤️",
                "💘",
                "✨"
            ];


            heart.innerText =
                hearts[
                    Math.floor(
                        Math.random() * hearts.length
                    )
                ];


            heart.style.left =
                Math.random() * 100 + "vw";


            heart.style.animationDuration =
                (3 + Math.random() * 3) + "s";


            document.body.appendChild(heart);


            setTimeout(function() {

                heart.remove();

            }, 6000);


        }, i * 100);

    }

}

</script>

</body>
</html>
