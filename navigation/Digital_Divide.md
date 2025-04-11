---
layout: page
title: Digital Divide HW Aarush Gowda Code Snippets
description: 
permalink: /divide/
---

```javascript
function exploreDigitalDivide() {
  const metric = prompt(
    "Which digital divide metric would you like to explore?\n" +
    "1: Income-based internet access\n" +
    "2: Urban vs rural access\n" +
    "3: Age-based internet usage\n" +
    "4: Global connectivity rates"
  );

  const incomeData = {
    categories: ["Lowest 20%", "Second 20%", "Middle 20%", "Fourth 20%", "Highest 20%"],
    values: [62, 71, 80, 88, 95]
  };
  const locationData = {
    categories: ["Urban", "Rural"],
    values: [94, 83]
  };
  const ageData = {
    categories: ["18-29", "30-49", "50-64", "65+"],
    values: [97, 93, 88, 61]
  };
  const globalData = {
    categories: ["North America", "Europe", "Asia Pacific", "Latin America", "Middle East/Africa"],
    values: [90, 87, 54, 68, 40]
  };

  let data, title;
  switch(metric) {
    case "1": data = incomeData; title = "Internet Access by Income Level (%)"; break;
    case "2": data = locationData; title = "Urban vs Rural Internet Access (%)"; break;
    case "3": data = ageData; title = "Internet Usage by Age Group (%)"; break;
    case "4": data = globalData; title = "Internet Access by Region (%)"; break;
    default: alert("Invalid selection!"); return;
  }

  console.log(title);
  console.log("=".repeat(title.length));
  const maxValue = Math.max(...data.values);
  const maxBarLength = 40;
  for (let i = 0; i < data.categories.length; i++) {
    const barLength = Math.round((data.values[i] / maxValue) * maxBarLength);
    const bar = "█".repeat(barLength);
    console.log(`${data.categories[i].padEnd(12)}: ${bar} ${data.values[i]}%`);
  }
}
```

```javascript
function bridgeTheDivideGame() {
  console.log("===============================================");
  console.log("🌉 BRIDGE THE DIVIDE: Digital Inclusion Challenge");
  console.log("===============================================");

  let score = 0;
  const totalQuestions = 2;

  console.log("SCENARIO 1: Rural Connectivity");
  console.log("A rural community of 500 families is 50 miles from broadband.");
  console.log("What’s the best approach with $200,000?");
  console.log("A: Lay fiber\nB: Wireless tower\nC: Satellite\nD: Community center");

  const answer1 = prompt("Your choice (A/B/C/D):").toUpperCase();
  if (answer1 === "B") {
    console.log("✓ Correct! Wireless towers balance cost and coverage.");
    score++;
  } else {
    console.log("✗ Correct answer was B.");
  }

  console.log("\nSCENARIO 2: Digital Literacy");
  console.log("Urban area has affordable internet but low use (30%).");
  console.log("What’s the best action?");
  console.log("A: Lower cost more\nB: Free tablets\nC: Literacy workshops\nD: Tech hotline");

  const answer2 = prompt("Your choice (A/B/C/D):").toUpperCase();
  if (answer2 === "C") {
    console.log("✓ Correct! Workshops solve the skills barrier.");
    score++;
  } else {
    console.log("✗ Correct answer was C.");
  }

  console.log(`\nFinal Score: ${score}/${totalQuestions}`);
}
```