<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Game Tài Xỉu</title>
  <style>
    body { font-family: Arial; text-align: center; padding: 40px; background: #f2f2f2; }
    h1 { color: #333; }
    button { padding: 10px 20px; margin: 10px; font-size: 18px; cursor: pointer; }
    #result { margin-top: 20px; font-size: 22px; font-weight: bold; }
    .dice { font-size: 40px; margin: 5px; }
  </style>
</head>
<body>
  <h1>🎲 Game Tài Xỉu</h1>
  <p>Chọn cược:</p>
  <button onclick="playGame('Tài')">Tài</button>
  <button onclick="playGame('Xỉu')">Xỉu</button>
  <div id="diceArea"></div>
  <div id="result"></div>

  <script>
    function rollDice() {
      return Math.floor(Math.random() * 6) + 1;
    }

    function playGame(playerChoice) {
      const d1 = rollDice();
      const d2 = rollDice();
      const d3 = rollDice();
      const total = d1 + d2 + d3;

      let gameResult;
      if ((d1 === d2 && d2 === d3)) {
        gameResult = "Nhà cái ăn (Bộ ba)";
      } else if (total >= 4 && total <= 10) {
        gameResult = "Xỉu";
      } else if (total >= 11 && total <= 17) {
        gameResult = "Tài";
      }

      document.getElementById("diceArea").innerHTML =
        `<div class="dice">🎲 ${d1} 🎲 ${d2} 🎲 ${d3}</div>`;

      let finalMsg = `Tổng: ${total} → ${gameResult}<br>`;
      if (gameResult === playerChoice) {
        finalMsg += "✅ Bạn thắng!";
      } else if (gameResult === "Nhà cái ăn (Bộ ba)") {
        finalMsg += "❌ Bạn thua (Bộ ba).";
      } else {
        finalMsg += "❌ Bạn thua.";
      }

      document.getElementById("result").innerHTML = finalMsg;
    }
  </script>
</body>
</html>
