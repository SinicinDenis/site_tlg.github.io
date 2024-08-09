</html>
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ping Pong Game</title>
<style>
  body {
    margin: 0;
    padding: 0;
  }
  canvas {
    display: block;
    margin: auto;
  }
</style>
</head>
<body>

<canvas id="gameCanvas"></canvas>

<script>
  const canvas = document.getElementById('gameCanvas');
  const ctx = canvas.getContext('2d');

  // Размеры и начальные координаты мяча
  let ballX = canvas.width / 2;
  let ballY = canvas.height / 2;

  // Скорость мяча
  const ballSpeed = 5;

  function drawBall() {
    ctx.beginPath();
    ctx.arc(ballX, ballY, 10, 0, Math.PI * 2);
    ctx.fillStyle = 'white';
    ctx.fill();
    ctx.closePath();
  }

  function moveBall() {
    // Движение мяча вверх и вниз
    ballY += ballSpeed;

    // Проверка столкновения с верхней и нижней границей
    if (ballY <= 0 || ballY >= canvas.height) {
      ballSpeed *= -1;
    }

    // Обновление позиции мяча
    drawBall();

    // Задержка перед следующим кадром
    requestAnimationFrame(moveBall);
  }

  // Запуск движения мяча
  moveBall();
</script>

</body>
</html>
