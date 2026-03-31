<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>我的计时器</title>
    <style>
        body {
            font-family: Arial;
            text-align: center;
            margin-top: 100px;
        }
        #time {
            font-size: 60px;
            margin: 20px;
        }
        button {
            font-size: 20px;
            margin: 10px;
            padding: 10px 20px;
        }
    </style>
</head>
<body>

<h1>我的计时器 ⏱️</h1>
<div id="time">00:00</div>

<button onclick="start()">开始</button>
<button onclick="stop()">暂停</button>
<button onclick="reset()">重置</button>

<script>
let seconds = 0;
let interval = null;

function updateTime() {
    let min = String(Math.floor(seconds / 60)).padStart(2, '0');
    let sec = String(seconds % 60).padStart(2, '0');
    document.getElementById("time").innerText = `${min}:${sec}`;
}

function start() {
    if (interval) return;
    interval = setInterval(() => {
        seconds++;
        updateTime();
    }, 1000);
}

function stop() {
    clearInterval(interval);
    interval = null;
}

function reset() {
    stop();
    seconds = 0;
    updateTime();
}
</script>

</body>
</html>
