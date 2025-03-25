---
layout: page 
title: Volleyball Simulator
search_exclude: true
permalink: /vball/
---

<h2>Volleyball Rotations Simulator - Passion Project - AP SEMINAR 2</h2>
<p>
  This simulator displays half a volleyball court (bird's eye view) with the net at the top and a marked 10ft/3m attack line. The players (labeled by position) are arranged in two rows on your side of the court. You can drag and drop any player to reposition them, and for each player, drag the arrow handle to set a target location. When you click the <strong>Play</strong> button, each player will run (animate) from their current location to the target indicated by their arrow.
</p>

<style>
  /* Court styling */
  #volleyball-court {
    width: 800px;
    height: 400px;
    border: 2px solid #333;
    position: relative;
    margin-bottom: 10px;
    background: #f0f0f0;
  }

  /* Net styling at the top */
  #volleyball-net {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 4px;
    background: repeating-linear-gradient(
      to right,
      #333,
      #333 4px,
      #f0f0f0 4px,
      #f0f0f0 8px
    );
    z-index: 3;
  }

  /* Attack line styling */
  #attack-line {
    position: absolute;
    top: 133px; /* Approximate 3m from the net */
    left: 0;
    width: 100%;
    height: 2px;
    background-color: red;
    z-index: 3;
  }
  
  #attack-line-label {
    position: absolute;
    top: 135px;
    left: 10px;
    font-size: 10px;
    color: red;
    z-index: 3;
  }

  /* Player styling as circles */
  .player {
    width: 60px;
    height: 60px;
    color: white;
    text-align: center;
    line-height: 60px;
    position: absolute;
    border-radius: 50%;
    cursor: move;
    user-select: none;
    font-size: 12px;
    z-index: 4;
  }

  /* SVG overlay for arrows */
  #arrow-overlay {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 2;
  }
  /* Ensure arrow handles can receive pointer events */
  .arrow-handle {
    pointer-events: auto;
    cursor: pointer;
  }
</style>

<div id="volleyball-court">
  <div id="volleyball-net"></div>
  <div id="attack-line"></div>
  <div id="attack-line-label">10ft/3m</div>
  
  <!-- SVG overlay for arrows -->
  <svg id="arrow-overlay" width="800" height="400">
    <defs>
      <marker id="arrowhead" markerWidth="10" markerHeight="7" refX="0" refY="3.5" orient="auto">
        <polygon points="0 0, 10 3.5, 0 7" fill="black" />
      </marker>
    </defs>
  </svg>

  <!-- Players -->
  <!-- Back row (closer to baseline) -->
  <div id="player1" class="player" draggable="true" style="left: 150px; top: 300px; background-color: #2196F3;">S</div>
  <div id="player2" class="player" draggable="true" style="left: 370px; top: 300px; background-color: #F44336;">L</div>
  <div id="player3" class="player" draggable="true" style="left: 590px; top: 300px; background-color: #FF9800;">OH2</div>
  <!-- Front row (closer to the net) -->
  <div id="player4" class="player" draggable="true" style="left: 150px; top: 100px; background-color: #9C27B0;">OH1</div>
  <div id="player5" class="player" draggable="true" style="left: 370px; top: 100px; background-color: #009688;">MB</div>
  <div id="player6" class="player" draggable="true" style="left: 590px; top: 100px; background-color: #FF5722;">OP</div>
</div>

<button id="playButton">Play</button>

<script>
  /* --- DRAG AND DROP FOR PLAYERS --- */
  var draggedElement = null;
  document.addEventListener("dragstart", function(event) {
    if (event.target.classList.contains("player")) {
      draggedElement = event.target;
      event.target.style.opacity = 0.5;
    }
  }, false);
  
  document.addEventListener("dragend", function(event) {
    if (event.target.classList.contains("player")) {
      event.target.style.opacity = "";
      updateArrowForPlayer(event.target.id);
    }
  }, false);
  
  var court = document.getElementById("volleyball-court");
  court.addEventListener("dragover", function(event) {
    event.preventDefault();
  }, false);
  
  court.addEventListener("drop", function(event) {
    event.preventDefault();
    if (draggedElement) {
      var rect = court.getBoundingClientRect();
      var offsetX = event.clientX - rect.left;
      var offsetY = event.clientY - rect.top;
      draggedElement.style.left = (offsetX - draggedElement.offsetWidth / 2) + "px";
      draggedElement.style.top = (offsetY - draggedElement.offsetHeight / 2) + "px";
      updateArrowForPlayer(draggedElement.id);
    }
  }, false);
  
  /* --- ARROW HANDLING --- */
  var playerArrows = {}; // holds arrow line and handle for each player
  var svgOverlay = document.getElementById("arrow-overlay");
  
  // Initialize arrow for each player
  function initArrows() {
    var players = document.getElementsByClassName("player");
    for (var i = 0; i < players.length; i++) {
      var player = players[i];
      var playerId = player.id;
      // Calculate player's center based on its style
      var centerX = parseFloat(player.style.left) + player.offsetWidth / 2;
      var centerY = parseFloat(player.style.top) + player.offsetHeight / 2;
      
      // Default target: 50px below the player (ensuring it stays within the court)
      var targetX = centerX;
      var targetY = Math.min(centerY + 50, court.clientHeight);
      
      // Create SVG line element for the arrow
      var line = document.createElementNS("http://www.w3.org/2000/svg", "line");
      line.setAttribute("x1", centerX);
      line.setAttribute("y1", centerY);
      line.setAttribute("x2", targetX);
      line.setAttribute("y2", targetY);
      line.setAttribute("stroke", "black");
      line.setAttribute("stroke-width", "2");
      line.setAttribute("marker-end", "url(#arrowhead)");
      svgOverlay.appendChild(line);
      
      // Create SVG circle for the arrow handle
      var handle = document.createElementNS("http://www.w3.org/2000/svg", "circle");
      handle.setAttribute("cx", targetX);
      handle.setAttribute("cy", targetY);
      handle.setAttribute("r", 6);
      handle.setAttribute("fill", "black");
      handle.setAttribute("class", "arrow-handle");
      handle.setAttribute("data-player", playerId);
      svgOverlay.appendChild(handle);
      
      // Save the arrow objects
      playerArrows[playerId] = { line: line, handle: handle };
      
      // Add drag events for the arrow handle
      addHandleDragEvents(handle);
    }
  }
  
  // Custom dragging for SVG arrow handles
  var currentDraggedHandle = null;
  function addHandleDragEvents(handle) {
    handle.addEventListener("mousedown", function(event) {
      currentDraggedHandle = handle;
      event.stopPropagation();
      event.preventDefault();
    });
  }
  
  document.addEventListener("mousemove", function(event) {
    if (currentDraggedHandle) {
      var svgRect = svgOverlay.getBoundingClientRect();
      var newX = event.clientX - svgRect.left;
      var newY = event.clientY - svgRect.top;
      currentDraggedHandle.setAttribute("cx", newX);
      currentDraggedHandle.setAttribute("cy", newY);
      
      // Update the corresponding arrow line's end point
      var playerId = currentDraggedHandle.getAttribute("data-player");
      var arrow = playerArrows[playerId];
      arrow.line.setAttribute("x2", newX);
      arrow.line.setAttribute("y2", newY);
    }
  });
  
  document.addEventListener("mouseup", function(event) {
    if (currentDraggedHandle) {
      currentDraggedHandle = null;
    }
  });
  
  // Update the starting point of the arrow line based on the player's current position
  function updateArrowForPlayer(playerId) {
    var player = document.getElementById(playerId);
    var centerX = parseFloat(player.style.left) + player.offsetWidth / 2;
    var centerY = parseFloat(player.style.top) + player.offsetHeight / 2;
    var arrow = playerArrows[playerId];
    arrow.line.setAttribute("x1", centerX);
    arrow.line.setAttribute("y1", centerY);
  }
  
  /* --- ANIMATION --- */
  // Animate a single player's movement toward its arrow handle (target)
  function animatePlayer(player) {
    var playerId = player.id;
    var arrow = playerArrows[playerId];
    var targetX = parseFloat(arrow.handle.getAttribute("cx"));
    var targetY = parseFloat(arrow.handle.getAttribute("cy"));
    
    // Get current center position of the player
    var currentX = parseFloat(player.style.left) + player.offsetWidth / 2;
    var currentY = parseFloat(player.style.top) + player.offsetHeight / 2;
    
    var dx = targetX - currentX;
    var dy = targetY - currentY;
    var distance = Math.sqrt(dx*dx + dy*dy);
    var speed = 3; // pixels per frame
  
    if (distance < speed) {
      // Arrived: set final position
      player.style.left = (targetX - player.offsetWidth / 2) + "px";
      player.style.top = (targetY - player.offsetHeight / 2) + "px";
      updateArrowForPlayer(playerId);
      return;
    }
    var moveX = (dx / distance) * speed;
    var moveY = (dy / distance) * speed;
    var newCenterX = currentX + moveX;
    var newCenterY = currentY + moveY;
    player.style.left = (newCenterX - player.offsetWidth / 2) + "px";
    player.style.top = (newCenterY - player.offsetHeight / 2) + "px";
    updateArrowForPlayer(playerId);
    requestAnimationFrame(function() {
      animatePlayer(player);
    });
  }
  
  // When "Play" is clicked, animate every player moving toward its target
  document.getElementById("playButton").addEventListener("click", function() {
    var players = document.getElementsByClassName("player");
    for (var i = 0; i < players.length; i++) {
      animatePlayer(players[i]);
    }
  });
  
  // Initialize arrow handles once the page loads
  window.onload = function() {
    initArrows();
  };
</script>
```javascript
// Initialize arrow handles once the page loads
window.onload = function() {
  initArrows();
  addEventListenersToPlayers();
};

// Custom dragging for SVG arrow handles
var currentDraggedHandle = null;
function addHandleDragEvents(handle) {
  handle.addEventListener("mousedown", function(event) {
    currentDraggedHandle = handle;
    event.stopPropagation();
    event.preventDefault();
  });
}

// Add event listeners to players
function addEventListenersToPlayers() {
  var players = document.getElementsByClassName("player");
  for (var i = 0; i < players.length; i++) {
    players[i].addEventListener("dragstart", function(event) {
      event.target.style.opacity = 0.5;
    });
    players[i].addEventListener("dragend", function(event) {
      event.target.style.opacity = "";
      updateArrowForPlayer(event.target.id);
    });
  }
}

// Update the starting point of the arrow line based on the player's current position
function updateArrowForPlayer(playerId) {
  var player = document.getElementById(playerId);
  var centerX = parseFloat(player.style.left) + player.offsetWidth / 2;
  var centerY = parseFloat(player.style.top) + player.offsetHeight / 2;
  var arrow = playerArrows[playerId];
  arrow.line.setAttribute("x1", centerX);
  arrow.line.setAttribute("y1", centerY);
}

// Animate a single player's movement toward its arrow handle (target)
function animatePlayer(player) {
  var playerId = player.id;
  var arrow = playerArrows[playerId];
  var targetX = parseFloat(arrow.handle.getAttribute("cx"));
  var targetY = parseFloat(arrow.handle.getAttribute("cy"));
  
  // Get current center position of the player
  var currentX = parseFloat(player.style.left) + player.offsetWidth / 2;
  var currentY = parseFloat(player.style.top) + player.offsetHeight / 2;
  
  var dx = targetX - currentX;
  var dy = targetY - currentY;
  var distance = Math.sqrt(dx*dx + dy*dy);
  var speed = 3; // pixels per frame
  
  if (distance < speed) {
    // Arrived: set final position
    player.style.left = (targetX - player.offsetWidth / 2) + "px";
    player.style.top = (targetY - player.offsetHeight / 2) + "px";
    updateArrowForPlayer(playerId);
    return;
  }
  var moveX = (dx / distance) * speed;
  var moveY = (dy / distance) * speed;
  var newCenterX = currentX + moveX;
  var newCenterY = currentY + moveY;
  player.style.left = (newCenterX - player.offsetWidth / 2) + "px";
  player.style.top = (newCenterY - player.offsetHeight / 2) + "px";
  updateArrowForPlayer(playerId);
  requestAnimationFrame(function() {
    animatePlayer(player);
  });
}

// When "Play" is clicked, animate every player moving toward its target
document.getElementById("playButton").addEventListener("click", function() {
  var players = document.getElementsByClassName("player");
  for (var i = 0; i < players.length; i++) {
    animatePlayer(players[i]);
  }
});

// Initialize arrow handles
function initArrows() {
  var players = document.getElementsByClassName("player");
  for (var i = 0; i < players.length; i++) {
    var player = players[i];
    var playerId = player.id;
    // Calculate player's center based on its style
    var centerX = parseFloat(player.style.left) + player.offsetWidth / 2;
    var centerY = parseFloat(player.style.top) + player.offsetHeight / 2;
    
    // Default target: 50px below the player (ensuring it stays within the court)
    var targetX = centerX;
    var targetY = Math.min(centerY + 50, court.clientHeight);
    
    // Create SVG line element for the arrow
    var line = document.createElementNS("http://www.w3.org/2000/svg", "line");
    line.setAttribute("x1", centerX);
    line.setAttribute("y1", centerY);
    line.setAttribute("x2", targetX);
    line.setAttribute("y2", targetY);
    line.setAttribute("stroke", "black");
    line.setAttribute("stroke-width", "2");
    line.setAttribute("marker-end", "url(#arrowhead)");
    svgOverlay.appendChild(line);
    
    // Create SVG circle for the arrow handle
    var handle = document.createElementNS("http://www.w3.org/2000/svg", "circle");
    handle.setAttribute("cx", targetX);
    handle.setAttribute("cy", targetY);
    handle.setAttribute("r", 6);
    handle.setAttribute("fill", "black");
    handle.setAttribute("class", "arrow-handle");
    handle.setAttribute("data-player", playerId);
    svgOverlay.appendChild(handle);
    
    // Save the arrow objects
    playerArrows[playerId] = { line: line, handle: handle };
    
    // Add drag events for the arrow handle
    addHandleDragEvents(handle);
  }
}

// DRAG AND DROP FOR PLAYERS
var draggedElement = null;
document.addEventListener("dragstart", function(event) {
  if (event.target.classList.contains("player")) {
    draggedElement = event.target;
  }
}, false);
  
document.addEventListener("dragend", function(event) {
  if (event.target.classList.contains("player")) {
    event.target.style.opacity = "";
    updateArrowForPlayer(event.target.id);
  }
}, false);
  
var court = document.getElementById("volleyball-court");
court.addEventListener("dragover", function(event) {
  event.preventDefault();
}, false);
  
court.addEventListener("drop", function(event) {
  event.preventDefault();
  if (draggedElement) {
    var rect = court.getBoundingClientRect();
    var offsetX = event.clientX - rect.left;
    var offsetY = event.clientY - rect.top;
    draggedElement.style.left = (offsetX - draggedElement.offsetWidth / 2) + "px";
    draggedElement.style.top = (offsetY - draggedElement.offsetHeight / 2) + "px";
    updateArrowForPlayer(draggedElement.id);
  }
}, false);

// Handle mouse move and up events for arrow handles
document.addEventListener("mousemove", function(event) {
  if (currentDraggedHandle) {
    var svgRect = svgOverlay.getBoundingClientRect();
    var newX = event.clientX - svgRect.left;
    var newY = event.clientY - svgRect.top;
    currentDraggedHandle.setAttribute("cx", newX);
    currentDraggedHandle.setAttribute("cy", newY);
    
    // Update the corresponding arrow line's end point
    var playerId = currentDraggedHandle.getAttribute("data-player");
    var arrow = playerArrows[playerId];
    arrow.line.setAttribute("x2", newX);
    arrow.line.setAttribute("y2", newY);
  }
});

document.addEventListener("mouseup", function(event) {
  if (currentDraggedHandle) {
    currentDraggedHandle = null;
  }
});
```