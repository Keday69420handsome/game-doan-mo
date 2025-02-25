<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trốn Tìm với Bot</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            margin: 50px;
        }

        #game-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            margin: auto;
        }

        input {
            padding: 10px;
            width: 80%;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
            text-align: center;
        }

        button {
            padding: 10px 20px;
            background-color: #28a745;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
            font-size: 16px;
        }

        button:hover {
            background-color: #218838;
        }

        #message {
            font-size: 18px;
            font-weight: bold;
            margin-top: 15px;
        }
    </style>
</head>
<body>
    <div id="game-container">
        <h2>🔍 Trốn Tìm với Bot</h2>
        <p>Hãy đoán xem bot đang trốn ở đâu (1-100)!</p>
        <input type="number" id="guess" min="1" max="100" placeholder="Nhập số...">
        <button onclick="checkGuess()">Đoán</button>
        <p id="message"></p>
    </div>
    <script>
        let botLocation = Math.floor(Math.random() * 100) + 1;
        let attempts = 0;
        let gameOver = false; // Biến kiểm tra trạng thái game

        function checkGuess() {
            if (gameOver) return; // Nếu game kết thúc, không cho đoán nữa

            let guessInput = document.getElementById("guess");
            let message = document.getElementById("message");
            let guess = parseInt(guessInput.value);
            attempts++;

            if (isNaN(guess) || guess < 1 || guess > 100) {
                message.innerHTML = "🚫 Vui lòng nhập số trong khoảng 1-100!";
                return;
            }

            if (guess < botLocation) {
                message.innerHTML = "📈 Bot đang ở vị trí cao hơn!";
            } else if (guess > botLocation) {
                message.innerHTML = "📉 Bot đang ở vị trí thấp hơn!";
            } else {
                message.innerHTML = `🎉 Chúc mừng! Bạn đã tìm thấy bot sau ${attempts} lần đoán!`;
                gameOver = true; // Đánh dấu trò chơi đã kết thúc
                return;
            }

            // Xóa nội dung input để nhập lại số mới
            guessInput.value = "";
        }
    </script>
</body>
</html>
