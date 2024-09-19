---
layout: page 
title: Snake Game
search_exclude: true
permalink: /snake_game/
---

# Simple Snake Game

<canvas id="gameCanvas" width="400" height="400" style="border:1px solid black;"></canvas>
<button id="resetButton" style="display: block; margin: 10px auto;">Reset Game</button>

<script>
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

const box = 20; // Size of the box
let snake, direction, food, game;

function initializeGame() {
    snake = [{ x: 9 * box, y: 9 * box }];
    direction = 'RIGHT';
    food = spawnFood();
    clearInterval(game);
    game = setInterval(draw, 100);
}

document.addEventListener('keydown', changeDirection);
document.getElementById('resetButton').addEventListener('click', initializeGame);

function changeDirection(event) {
    if (event.keyCode === 37 && direction !== 'RIGHT') direction = 'LEFT';
    else if (event.keyCode === 38 && direction !== 'DOWN') direction = 'UP';
    else if (event.keyCode === 39 && direction !== 'LEFT') direction = 'RIGHT';
    else if (event.keyCode === 40 && direction !== 'UP') direction = 'DOWN';
}

function spawnFood() {
    return {
        x: Math.floor(Math.random() * (canvas.width / box)) * box,
        y: Math.floor(Math.random() * (canvas.height / box)) * box,
    };
}

function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    for (let i = 0; i < snake.length; i++) {
        ctx.fillStyle = (i === 0) ? 'green' : 'lightgreen';
        ctx.fillRect(snake[i].x, snake[i].y, box, box);
        ctx.strokeStyle = 'darkgreen';
        ctx.strokeRect(snake[i].x, snake[i].y, box, box);
    }

    ctx.fillStyle = 'red';
    ctx.fillRect(food.x, food.y, box, box);

    let snakeX = snake[0].x;
    let snakeY = snake[0].y;

    if (direction === 'LEFT') snakeX -= box;
    if (direction === 'UP') snakeY -= box;
    if (direction === 'RIGHT') snakeX += box;
    if (direction === 'DOWN') snakeY += box;

    if (snakeX === food.x && snakeY === food.y) {
        food = spawnFood();
    } else {
        snake.pop();
    }

    const newHead = { x: snakeX, y: snakeY };

    if (collision(newHead, snake)) {
        clearInterval(game);
        alert('Game Over!');
    }

    snake.unshift(newHead);
}

function collision(head, array) {
    return array.some(segment => segment.x === head.x && segment.y === head.y);
}

// Initialize the game when the page loads
initializeGame();
</script>
