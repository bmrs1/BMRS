# <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Text to Speech Converter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            background: #fff;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        textarea {
            width: 100%;
            height: 150px;
            padding: 10px;
            margin-bottom: 10px;
            font-size: 16px;
        }
        button {
            padding: 10px 15px;
            font-size: 16px;
            cursor: pointer;
            background-color: #5cb85c;
            color: white;
            border: none;
            border-radius: 5px;
            margin-right: 10px;
        }
        label {
            display: block;
            margin: 10px 0 5px;
        }
        input[type="range"] {
            width: 100%;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Text to Speech Converter</h1>
        <textarea id="text-input" placeholder="Enter your text here..."></textarea>

        <label for="speed">Speed:</label>
        <input type="range" id="speed" min="0.1" max="2" step="0.1" value="1">
        <span id="speed-value">1</span>

        <label for="pitch">Pitch:</label>
        <input type="range" id="pitch" min="0" max="2" step="0.1" value="1">
        <span id="pitch-value">1</span>

        <button id="speak-button">Convert to Speech</button>
    </div>

    <!-- Include the ResponsiveVoice API -->
    <script src="https://code.responsivevoice.org/responsivevoice.js?key=YOUR_API_KEY"></script>

    <script>
        document.getElementById('speed').addEventListener('input', function() {
            document.getElementById('speed-value').textContent = this.value;
        });

        document.getElementById('pitch').addEventListener('input', function() {
            document.getElementById('pitch-value').textContent = this.value;
        });

        document.getElementById('speak-button').addEventListener('click', function() {
            var text = document.getElementById('text-input').value;
            var speed = document.getElementById('speed').value;
            var pitch = document.getElementById('pitch').value;

            if(text.trim() !== "") {
                responsiveVoice.speak(text, "UK English Male", {
                    rate: speed, // Speed of speech
                    pitch: pitch // Pitch of speech
                });
            } else {
                alert("Please enter some text to convert!");
            }
        });
    </script>
</body>
</html>
