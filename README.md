<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Cler Page</title>
  <link href="https://fonts.googleapis.com/css2?family=Open+Sans&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      background-color: black;
      color: white;
      font-family: 'Open Sans', sans-serif;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
      text-align: center;
    }

    h1 {
      font-size: 2em;
      margin-bottom: 40px;
    }

    .buttons {
      display: flex;
      gap: 20px;
    }

    button {
      padding: 20px 40px;
      font-size: 1.2em;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    #yesBtn {
      background-color: #28a745;
      color: white;
    }

    #noBtn {
      background-color: #dc3545;
      color: white;
      z-index: 1;
    }

    #yayMessage {
      display: none;
      font-size: 3em;
      color: yellow;
      z-index: 2;
    }

    .fullScreenNo {
      position: absolute;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      font-size: 10vw !important;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 10;
    }
  </style>
</head>
<body>
  <h1>cler, km stress yh sm aku?</h1>
  <div class="buttons">
    <button id="yesBtn">Yes</button>
    <button id="noBtn">No</button>
  </div>
  <div id="yayMessage">YAYYYY</div>

  <script>
    const yesBtn = document.getElementById('yesBtn');
    const noBtn = document.getElementById('noBtn');
    const yayMessage = document.getElementById('yayMessage');

    let clickCount = 0;
    const maxClicks = 10;

    yesBtn.addEventListener('click', () => {
      clickCount++;
      let scaleYes = Math.max(0.2, 1 - (clickCount * 0.07));
      let scaleNo = 1 + (clickCount * 0.2);

      yesBtn.style.transform = `scale(${scaleYes})`;
      noBtn.style.transform = `scale(${scaleNo})`;

      if (clickCount >= maxClicks) {
        noBtn.classList.add('fullScreenNo');
        noBtn.textContent = "NO";
      }
    });

    noBtn.addEventListener('click', () => {
      document.querySelector('.buttons').style.display = 'none';
      yayMessage.style.display = 'block';
    });
  </script>
</body>
</html>
