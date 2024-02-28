<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Snake Game</title>
  <style>
    canvas {
      border: 1px solid black;
      display: block;
      margin: 0 auto;
    }
  </style>
</head>
<body>
  <h1 align="center">Hi 👋, I'm Avinash Kumar</h1>
  <h3 align="center">A passionate frontend developer</h3>
  <p align="center">
    <img src="https://media.giphy.com/media/ZVik7pBtu9dNS/giphy.gif" alt="Developer GIF" width="350" height="250"/>
  </p>

  <h3 align="left">Connect with me:</h3>
  <p align="left">
    <!-- Add your social media links here -->
  </p>

  <h3 align="left">Languages and Tools:</h3>
  <p align="left">
    <!-- Your existing tools icons -->
  </p>

  <canvas id="snakeCanvas" width="400" height="400"></canvas>

  <script>
    // JavaScript for the snake game

    // Your game logic goes here
    // For simplicity, I'm not including the entire game code
    // You can find complete implementations online or create your own

    // Example code for creating a simple snake game
    const canvas = document.getElementById('snakeCanvas');
    const ctx = canvas.getContext('2d');

    let snake = [{x: 10, y: 10}];
    let food = {x: 5, y: 5};
    let direction = 'right';

    function draw() {
      // clear canvas
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // draw snake
      ctx.fillStyle = 'green';
      snake.forEach(segment => {
        ctx.fillRect(segment.x * 20, segment.y * 20, 20, 20);
      });

      // draw food
      ctx.fillStyle = 'red';
      ctx.fillRect(food.x * 20, food.y * 20, 20, 20);
    }

    function update() {
      // update snake position
      const head = { ...snake[0] };
      switch (direction) {
        case 'up':
          head.y -= 1;
          break;
        case 'down':
          head.y += 1;
          break;
        case 'left':
          head.x -= 1;
          break;
        case 'right':
          head.x += 1;
          break;
      }
      snake.unshift(head);

      // check if snake eats food
      if (head.x === food.x && head.y === food.y) {
        // generate new food
        food.x = Math.floor(Math.random() * canvas.width / 20);
        food.y = Math.floor(Math.random() * canvas.height / 20);
      } else {
        // remove tail
        snake.pop();
      }
    }

    function gameLoop() {
      draw();
      update();
      setTimeout(gameLoop, 100); // loop every 100ms
    }

    gameLoop();
  </script>
</body>
</html>
