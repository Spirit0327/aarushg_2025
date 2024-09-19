---
layout: page
title: Simple Game
permalink: /game/
---

<h1>Simple Game</h1>
<p>Welcome to the game page! Below are two simple games for you to play.</p>

<!-- Old Game -->
<div id="old-game-container" style="text-align: center; margin-top: 20px;">
  <h2>Game 1: Start Game Button</h2>
  <button onclick="alert('START THE GAME OR A VIRUS WILL DOWNLOAD!')" id="game-start" style="padding: 10px 20px; font-size: 16px; border: none; border-radius: 5px; background-color: #28a745; color: white; cursor: pointer;">
    Start Game
  </button>
  <p id="game-status" style="font-size: 18px; margin-top: 20px;"></p>
</div>

<script>
  document.getElementById('game-start').addEventListener('click', function() {
    document.getElementById('game-status').textContent = 'Here’s where the game logic would go, but I want to make your life hard.';
  });
</script>

<hr>

<!-- Cookie Clicker Game -->
<div id="cookie-game-container" style="text-align: center; margin-top: 20px;">
  <h2>Game 2: Cookie Clicker</h2>
  <img id="cookie" src="{{site.baseurl}}/images/cookie.png" alt="Cookie" width="200px" height="200px" style="cursor: pointer;">
  <img source>
  <p>Cookies clicked: <span id="counter">0</span></p>
</div>

<script>
  let counter = 0;
  
  document.getElementById('cookie').addEventListener('click', function() {
    counter++;
    document.getElementById('counter').textContent = counter;
  });
</script>
