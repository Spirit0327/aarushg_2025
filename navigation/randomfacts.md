---
layout: page
title: Random Volleyball Facts Generator
description: 
permalink: /randomfacts/
---

# Random Volleyball Facts 🏐

Click the button to learn a random fun fact about volleyball!

<button onclick="generateFact()" style="padding: 10px 20px; font-size: 16px; border: none; border-radius: 5px; background-color: #007bff; color: white; cursor: pointer;">Get Random Fact</button>

<p id="fact" style="font-size: 18px; margin-top: 20px;"></p>

<script>
  const facts = [
    "Volleyball was invented in 1895 by William G. Morgan.",
    "A volleyball match is played with six players on each team.",
    "The first volleyball game took place at Springfield College in 1896.",
    "Beach volleyball became an Olympic sport in 1996.",
    "The record for the longest volleyball game is 85 hours!"
  ];

  function generateFact() {
    const randomIndex = Math.floor(Math.random() * facts.length);
    document.getElementById("fact").innerText = facts[randomIndex];
  }
</script>