# Stopwatch-application
# Developed By : ADITYAH  M S
# Reg.no : 212223220002

# Properties Included :

Buttons to Start, Pause, and Reset.

Displays time in the format: MM : SS : MS (minutes, seconds, milliseconds).

The time updates dynamically without page refresh.


# Code
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Stopwatch</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #111;
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .stopwatch {
      text-align: center;
      background: #222;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.6);
    }
    .time {
      font-size: 3rem;
      letter-spacing: 2px;
      margin-bottom: 20px;
    }
    .buttons button {
      padding: 10px 20px;
      margin: 5px;
      font-size: 1rem;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.2s;
    }
    .buttons button:hover {
      opacity: 0.8;
    }
    .start { background: #28a745; color: white; }
    .pause { background: #ffc107; color: black; }
    .reset { background: #dc3545; color: white; }
  </style>
</head>
<body>
  <div class="stopwatch">
    <div class="time" id="display">00 : 00 : 000</div>
    <div class="buttons">
      <button class="start" onclick="start()">Start</button>
      <button class="pause" onclick="pause()">Pause</button>
      <button class="reset" onclick="reset()">Reset</button>
    </div>
  </div>

  <script>
    let startTime = 0;
    let elapsedTime = 0;
    let timerInterval;

    function updateTime() {
      const currentTime = Date.now() - startTime + elapsedTime;
      const minutes = Math.floor(currentTime / 60000);
      const seconds = Math.floor((currentTime % 60000) / 1000);
      const milliseconds = currentTime % 1000;

      document.getElementById("display").textContent =
        (minutes < 10 ? "0" : "") + minutes + " : " +
        (seconds < 10 ? "0" : "") + seconds + " : " +
        milliseconds.toString().padStart(3, "0");
    }

    function start() {
      if (!timerInterval) {
        startTime = Date.now();
        timerInterval = setInterval(updateTime, 10);
      }
    }

    function pause() {
      if (timerInterval) {
        clearInterval(timerInterval);
        timerInterval = null;
        elapsedTime += Date.now() - startTime;
      }
    }

    function reset() {
      clearInterval(timerInterval);
      timerInterval = null;
      startTime = 0;
      elapsedTime = 0;
      document.getElementById("display").textContent = "00 : 00 : 000";
    }
  </script>
</body>
</html>
```
# OUTPUT :

<img width="1914" height="1008" alt="Screenshot 2025-09-03 041300" src="https://github.com/user-attachments/assets/83cf5aaf-1ce0-4127-9386-0f53c73d5ce8" />
<img width="1919" height="1012" alt="Screenshot 2025-09-03 041315" src="https://github.com/user-attachments/assets/5368263d-9246-4d3d-bbed-8593878cda7c" />

