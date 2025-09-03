# stop-watch--app

## code
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Stopwatch</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #f0f4f8;
      font-family: Arial, sans-serif;
    }

    .stopwatch {
      background: #fff;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.2);
      text-align: center;
    }

    .time {
      font-size: 2.5rem;
      font-weight: bold;
      margin-bottom: 20px;
    }

    button {
      padding: 10px 20px;
      margin: 5px;
      font-size: 1rem;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.2s ease;
    }

    button:hover {
      opacity: 0.8;
    }

    .start { background: #4caf50; color: white; }
    .pause { background: #ff9800; color: white; }
    .reset { background: #f44336; color: white; }
  </style>
</head>
<body>
  <div class="stopwatch">
    <div class="time" id="display">00 : 00 : 000</div>
    <button class="start" id="startBtn">Start</button>
    <button class="pause" id="pauseBtn">Pause</button>
    <button class="reset" id="resetBtn">Reset</button>
  </div>

  <script>
    let startTime, updatedTime, difference, tInterval;
    let running = false;

    const display = document.getElementById("display");
    const startBtn = document.getElementById("startBtn");
    const pauseBtn = document.getElementById("pauseBtn");
    const resetBtn = document.getElementById("resetBtn");

    function startTimer() {
      if (!running) {
        startTime = new Date().getTime() - (difference || 0);
        tInterval = setInterval(updateDisplay, 10);
        running = true;
      }
    }

    function pauseTimer() {
      if (running) {
        clearInterval(tInterval);
        difference = new Date().getTime() - startTime;
        running = false;
      }
    }

    function resetTimer() {
      clearInterval(tInterval);
      running = false;
      difference = 0;
      display.innerHTML = "00 : 00 : 000";
    }

    function updateDisplay() {
      updatedTime = new Date().getTime() - startTime;
      let minutes = Math.floor((updatedTime % (1000 * 60 * 60)) / (1000 * 60));
      let seconds = Math.floor((updatedTime % (1000 * 60)) / 1000);
      let milliseconds = updatedTime % 1000;

      minutes = (minutes < 10) ? "0" + minutes : minutes;
      seconds = (seconds < 10) ? "0" + seconds : seconds;
      milliseconds = milliseconds.toString().padStart(3, '0');

      display.innerHTML = `${minutes} : ${seconds} : ${milliseconds}`;
    }

    startBtn.addEventListener("click", startTimer);
    pauseBtn.addEventListener("click", pauseTimer);
    resetBtn.addEventListener("click", resetTimer);
  </script>
</body>
</html>
```
## Output
<img width="1919" height="1023" alt="Screenshot 2025-09-03 101244" src="https://github.com/user-attachments/assets/e89d2dce-6aaf-4c85-a580-5882e3cffcb9" />

<img width="1917" height="1005" alt="Screenshot 2025-09-03 101309" src="https://github.com/user-attachments/assets/0e353e59-a972-4638-8bbe-e1f8f43be49f" />

<img width="1919" height="1020" alt="Screenshot 2025-09-03 101319" src="https://github.com/user-attachments/assets/7707cccd-611f-4a3d-9de2-7d867ca4eda0" />
