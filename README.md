<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Circle</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: black;
            transition: background-color 1s;
        }

        h1 {
            font-size: 4rem;
            text-align: center;
            transition: color 1s, text-shadow 1s, border 1s, font-family 1s;
        }

        #time {
            font-size: 2rem;
            text-align: center;
            transition: opacity 1s;
        }
    </style>
</head>
<body>
    <div>
        <h1 id="title">Circus</h1>
        <p id="time"></p>
        <button id="btn">Start</button>
    </div>

    <script>
        // Get DOM elements
        const body = document.querySelector('body');
        const title = document.querySelector('#title');
        const timeElement = document.querySelector('#time');
        const btn = document.querySelector('#btn');

        // Array of font families
        const fontFamilies = ['Arial', 'Times New Roman', 'Verdana', 'Courier New', 'Georgia'];

        // Function to generate random color
        function getRandomColor() {
            return `#${Math.floor(Math.random() * 16777215).toString(16)}`;
        }

        // Function to get current time
        function getCurrentTime() {
            const now = new Date();
            return now.toLocaleTimeString();
        }

        // Function to update styles
        function updateStyles() {
            // Change background color
            body.style.backgroundColor = getRandomColor();

            // Change title color, font family, text shadow, and border
            title.style.color = getRandomColor();
            title.style.fontFamily = fontFamilies[Math.floor(Math.random() * fontFamilies.length)];
            title.style.textShadow = `0 0 10px ${getRandomColor()}`;
            title.style.border = Math.random() < 0.5 ? `5px solid ${getRandomColor()}` : 'none';

            // Toggle time visibility
            timeElement.style.opacity = Math.random() < 0.5 ? 1 : 0;
            timeElement.textContent = getCurrentTime();
        }

        let intervalId;

        // Start/stop function
        function toggleAnimation() {
            if (intervalId) {
                clearInterval(intervalId);
                btn.textContent = 'Start';
            } else {
                intervalId = setInterval(updateStyles, 1000);
                btn.textContent = 'Stop';
            }
        }

        // Event listener for button click
        btn.addEventListener('click', toggleAnimation);
    </script>
</body>
</html>
