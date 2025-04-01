---
layout: page 
title: Volleyball Simulator
search_exclude: true
permalink: /vball/
---

<h2>Volleyball Rotations Simulator - Passion Project - AP SEMINAR 2</h2>
<p>
  This simulator displays half a volleyball court (bird's eye view) with the net at the top and a marked 10ft/3m attack line. The players (labeled by position) are arranged in two rows on your side of the court. You can drag and drop any player to reposition them, and for each player, drag the arrow handle to set a target location. When you click the <strong>Play</strong> button, each player will run (animate) from their current location to the target indicated by their arrow. You can also toggle <strong>Tactic Mode</strong> to place strategy markers.
</p>

<style>
  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f9fafb;
    padding: 20px;
  }
  #volleyball-court {
    width: 800px;
    height: 400px;
    border: 2px solid #333;
    position: relative;
    margin-bottom: 10px;
    border-radius: 16px;
    background: linear-gradient(to bottom, #dbeafe, #f0f4f8);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
  }
  #volleyball-net {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 4px;
    background: repeating-linear-gradient(to right, #333, #333 4px, #f0f0f0 4px, #f0f0f0 8px);
    z-index: 3;
  }
  #attack-line {
    position: absolute;
    top: 133px;
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
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    border: 2px solid white;
  }
  .tactic-marker {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background-color: rgba(255, 0, 0, 0.6);
    position: absolute;
    z-index: 1;
    pointer-events: none;
  }
  #arrow-overlay {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 2;
  }
  .arrow-handle {
    pointer-events: auto;
    cursor: pointer;
  }
  .button-container {
    margin-top: 10px;
  }
  .button-container button {
    margin-right: 10px;
    background-color: #4CAF50;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  .button-container button:hover {
    background-color: #45a049;
  }
</style>

<div id="volleyball-court">
  <div id="volleyball-net"></div>
  <div id="attack-line"></div>
  <div id="attack-line-label">10ft/3m</div>
  <svg id="arrow-overlay" width="800" height="400">
    <defs>
      <marker id="arrowhead" markerWidth="10" markerHeight="7" refX="0" refY="3.5" orient="auto">
        <polygon points="0 0, 10 3.5, 0 7" fill="black" />
      </marker>
    </defs>
  </svg>
  <div id="player1" class="player" draggable="true" style="left: 150px; top: 300px; background-color: #2196F3;">S</div>
  <div id="player2" class="player" draggable="true" style="left: 370px; top: 300px; background-color: #F44336;">L</div>
  <div id="player3" class="player" draggable="true" style="left: 590px; top: 300px; background-color: #FF9800;">OH2</div>
  <div id="player4" class="player" draggable="true" style="left: 150px; top: 100px; background-color: #9C27B0;">OH1</div>
  <div id="player5" class="player" draggable="true" style="left: 370px; top: 100px; background-color: #009688;">MB</div>
  <div id="player6" class="player" draggable="true" style="left: 590px; top: 100px; background-color: #FF5722;">OP</div>
</div>
<div class="button-container">
  <button id="playButton">Play</button>
  <button id="tacticToggle">Tactic Mode</button>
</div>

<script>
  let playerArrows = {}, draggedElement = null, currentDraggedHandle = null;
  const svgOverlay = document.getElementById("arrow-overlay");
  const court = document.getElementById("volleyball-court");
  let tacticMode = false;

  function initArrows() {
    const players = document.getElementsByClassName("player");
    for (const player of players) {
      const id = player.id;
      const cx = parseFloat(player.style.left) + player.offsetWidth / 2;
      const cy = parseFloat(player.style.top) + player.offsetHeight / 2;
      const tx = cx;
      const ty = Math.min(cy + 50, court.clientHeight);

      const line = document.createElementNS("http://www.w3.org/2000/svg", "line");
      line.setAttribute("x1", cx); line.setAttribute("y1", cy);
      line.setAttribute("x2", tx); line.setAttribute("y2", ty);
      line.setAttribute("stroke", "black"); line.setAttribute("stroke-width", "2");
      line.setAttribute("marker-end", "url(#arrowhead)");
      svgOverlay.appendChild(line);

      const handle = document.createElementNS("http://www.w3.org/2000/svg", "circle");
      handle.setAttribute("cx", tx); handle.setAttribute("cy", ty);
      handle.setAttribute("r", 6); handle.setAttribute("fill", "black");
      handle.setAttribute("class", "arrow-handle");
      handle.setAttribute("data-player", id);
      svgOverlay.appendChild(handle);

      playerArrows[id] = { line, handle };

      handle.addEventListener("mousedown", e => {
        currentDraggedHandle = handle;
        e.preventDefault();
      });
    }
  }

  function updateArrowForPlayer(id) {
    const player = document.getElementById(id);
    const cx = parseFloat(player.style.left) + player.offsetWidth / 2;
    const cy = parseFloat(player.style.top) + player.offsetHeight / 2;
    const arrow = playerArrows[id];
    arrow.line.setAttribute("x1", cx);
    arrow.line.setAttribute("y1", cy);
  }

  function animatePlayer(player) {
    const id = player.id;
    const arrow = playerArrows[id];
    const tx = parseFloat(arrow.handle.getAttribute("cx"));
    const ty = parseFloat(arrow.handle.getAttribute("cy"));
    const cx = parseFloat(player.style.left) + player.offsetWidth / 2;
    const cy = parseFloat(player.style.top) + player.offsetHeight / 2;
    const dx = tx - cx;
    const dy = ty - cy;
    const dist = Math.sqrt(dx * dx + dy * dy);
    const speed = 3;
    if (dist < speed) {
      player.style.left = (tx - player.offsetWidth / 2) + "px";
      player.style.top = (ty - player.offsetHeight / 2) + "px";
      updateArrowForPlayer(id);
      return;
    }
    player.style.left = (cx + dx / dist * speed - player.offsetWidth / 2) + "px";
    player.style.top = (cy + dy / dist * speed - player.offsetHeight / 2) + "px";
    updateArrowForPlayer(id);
    requestAnimationFrame(() => animatePlayer(player));
  }

  document.getElementById("playButton").addEventListener("click", () => {
    const players = document.getElementsByClassName("player");
    for (const p of players) animatePlayer(p);
  });

  document.getElementById("tacticToggle").addEventListener("click", () => {
    tacticMode = !tacticMode;
    court.style.cursor = tacticMode ? "crosshair" : "default";
  });

  court.addEventListener("click", (e) => {
    if (!tacticMode) return;
    const rect = court.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    const marker = document.createElement("div");
    marker.className = "tactic-marker";
    marker.style.left = `${x - 10}px`;
    marker.style.top = `${y - 10}px`;
    court.appendChild(marker);
  });

  document.addEventListener("dragstart", e => {
    if (e.target.classList.contains("player")) {
      draggedElement = e.target;
      e.target.style.opacity = 0.5;
    }
  });

  document.addEventListener("dragend", e => {
    if (e.target.classList.contains("player")) {
      e.target.style.opacity = "";
      updateArrowForPlayer(e.target.id);
    }
  });

  court.addEventListener("dragover", e => e.preventDefault());
  court.addEventListener("drop", e => {
    e.preventDefault();
    if (draggedElement) {
      const rect = court.getBoundingClientRect();
      draggedElement.style.left = (e.clientX - rect.left - draggedElement.offsetWidth / 2) + "px";
      draggedElement.style.top = (e.clientY - rect.top - draggedElement.offsetHeight / 2) + "px";
      updateArrowForPlayer(draggedElement.id);
    }
  });

  document.addEventListener("mousemove", e => {
    if (currentDraggedHandle) {
      const svgRect = svgOverlay.getBoundingClientRect();
      const nx = e.clientX - svgRect.left;
      const ny = e.clientY - svgRect.top;
      currentDraggedHandle.setAttribute("cx", nx);
      currentDraggedHandle.setAttribute("cy", ny);
      const id = currentDraggedHandle.getAttribute("data-player");
      playerArrows[id].line.setAttribute("x2", nx);
      playerArrows[id].line.setAttribute("y2", ny);
    }
  });

  document.addEventListener("mouseup", () => currentDraggedHandle = null);
  window.onload = initArrows;
</script>
