<html>
<head>
    <meta charset="UTF-8">
    <title>Reaction Time Test</title>
    <style>
        body {
            background-color: #f2f2f2;
            font-family: Arial, sans-serif;
            color: #333;
            text-align: center;
        }
        h1 {
            margin-top: 50px;
            font-size: 36px;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 50px;
        }
        .dot {
            position: absolute;
            top: 0;
            left: 0;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: red;
            display: none;
            cursor: pointer;
        }
        .dot.green {
            background-color: green;
        }
        .timer {
            font-size: 48px;
            font-weight: bold;
            margin-bottom: 20px;
        }
        .contribute {
  display: inline-block;
  padding: 10px 20px;
  background-color: #333;
  color: #fff;
  font-size: 16px;
  cursor: pointer;
  border-radius: 20px;
  opacity: 0.8;
  transition: transform 0.2s ease-in-out;
  z-index: 1;
  position: fixed;
  left: 2%;
  bottom: 20px;

}


        .contribute:hover {
            transform: scale(1.2);
        
        }
    </style>
</head>
<body>
    <h1>Reaction Time Test</h1>
    <div class="container">
        <button id="startBtn">Start</button>
        <div class="timer"></div>
        <div class="dot"></div>
        <div id="feedback"></div>
    </div>
    <a class="contribute" href="https://github.com/TheFutureMillionaire2004/Donate.git" target="_blank">Contribute to future projects</a>

    <script>
    var startTime, reactionTime, dotTimeout, dotInterval;
var dot = document.querySelector('.dot');
var timer = document.querySelector('.timer');
var feedback = document.querySelector('#feedback');
var startBtn = document.querySelector('#startBtn');
var contributeLink = document.querySelector('.contribute');

function startTimer() {
    timer.innerHTML = "3";
    setTimeout(function() { timer.innerHTML = "2"; }, 1000);
    setTimeout(function() { timer.innerHTML = "1"; }, 2000);
    setTimeout(function() {
        timer.innerHTML = "Go!";
        startTime = new Date().getTime();
        dotInterval = setInterval(function() {
            dot.style.top = Math.floor(Math.random() * (window.innerHeight - dot.clientHeight)) + "px";
            dot.style.left = Math.floor(Math.random() * (window.innerWidth - dot.clientWidth)) + "px";
            dot.style.backgroundColor = "red";
            dot.style.display = "block";
            startTime = new Date().getTime();
            dotTimeout = setTimeout(function() {
                clearInterval(dotInterval);
            }, Math.floor(Math.random() * 9000) + 1000);
        }, Math.floor(Math.random() * 9000) + 1000);
    }, 3000);
}

function handleClick() {
    if (dot.style.display !== "none") {
        var endTime = new Date().getTime();
        reactionTime = (endTime - startTime) / 1000;
        feedback.innerHTML = "Your reaction time was " + reactionTime.toFixed(3) + " seconds!";
        feedback.style.color = "green";
        dot.style.backgroundColor = "green";
        dot.removeEventListener('click', handleClick);
        setTimeout(function() { dot.style.display = "none"; }, 1000);
        clearInterval(dotInterval);
        clearTimeout(dotTimeout);
        startBtn.innerHTML = "Restart";
    }
}

startBtn.addEventListener('click', function() {
    if (startBtn.innerHTML === "Restart") {
        location.reload();
    } else {
        startBtn.style.display = "none";
        startTimer();
    }
});

dot.addEventListener('click', handleClick);

contributeLink.addEventListener('mouseover', function() {
    contributeLink.style.opacity = "0.8";
    contributeLink.style.transform = "scale(1.2)";
});

contributeLink.addEventListener('mouseout', function() {
    contributeLink.style.opacity = "";
    contributeLink.style.transform = "";
});

contributeLink.addEventListener('click', function() {
    window.open("https://thefuturemillionaire2004.github.io/game/", "_blank");
});

</script>
