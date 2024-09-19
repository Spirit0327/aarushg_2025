---
layout: base
title: Aarush Gowda Home 
description: Home Page
hide: true
image: /images/mario_animation.png
---

Hello! I’m Aarush Gowda and I am a very passionate coder and am excited to share my journey with you!
Amazing Indian Music Below 🎵🎤: 

<!-- Include submenu from _includes to top of pages -->
{% include nav/home.html %}
{% assign sprite_file = site.baseurl | append: page.image %}
{% assign hash = site.data.mario_metadata %}  
{% assign pixels = 256 %}

<iframe style="border-radius:12px" src="https://open.spotify.com/embed/playlist/0zQ00nAz1o7l7dS31jf6N3?utm_source=generator" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>

<p id="mario" class="sprite"></p>
  
<style>
  .sprite {
    height: {{pixels}}px;
    width: {{pixels}}px;
    background-image: url('{{sprite_file}}');
    background-repeat: no-repeat;
  }

  #mario {
    background-position: calc({{animations[0].col}} * {{pixels}} * -1px) calc({{animations[0].row}} * {{pixels}}* -1px);
  }

  .dropdown-content {
    display: none;
    position: absolute;
    background-color: white;
    border: 1px solid #ccc;
    z-index: 1;
  }

  .dropdown-content.show {
    display: block;
  }

  .dropdown-content a {
    display: block;
    padding: 10px;
    text-decoration: none;
  }
</style>

<script>
  // Dropdown functionality
  function toggleDropdown() {
    const dropdown = document.getElementById("dropdown");
    dropdown.classList.toggle("show");
  }

  window.onclick = function(event) {
    if (!event.target.matches('.dropbtn')) {
      const dropdowns = document.getElementsByClassName("dropdown-content");
      for (let i = 0; i < dropdowns.length; i++) {
        const openDropdown = dropdowns[i];
        if (openDropdown.classList.contains('show')) {
          openDropdown.classList.remove('show');
        }
      }
    }
  }
</script>

<!-- Dropdown menu for game navigation -->
<div style="margin-top: 20px; text-align: center;">
  <div style="display: inline-block; position: relative;">
    <button class="dropbtn" onclick="toggleDropdown()" style="padding: 10px; font-size: 16px; border: none; border-radius: 5px; background-color: #007bff; color: white; cursor: pointer;">Games</button>
    <div id="dropdown" class="dropdown-content">
      <a href="game">Game</a>
      <a href="calculator">Calculator</a>
      <a href="snake">Snake</a>
    </div>
  </div>
</div>

<script src="https://utteranc.es/client.js"
        repo="aarushg_2025"
        issue-term="pathname"
        theme="github-dark"
        crossorigin="anonymous"
        async>
    </script>