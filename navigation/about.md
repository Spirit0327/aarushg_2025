---
layout: page
title: About Aarush Gowda
permalink: /about/
---

<!-- Adding fade-in effect for the hidden content -->
<button id="coding-experience-btn" style="background-color: #4CAF50; color: #ffffff; transition: transform 0.2s;" onmouseover="this.style.transform='scale(1.05)'" onmouseout="this.style.transform='scale(1)'">Coding Experience (CLICK ME!)</button>
<div id="coding-experience-text" style="display: none; opacity: 0; transition: opacity 1s;">
  I have been coding for 3 years now, starting with simple blocks and then moving forward to HTML, CSS, and JS! This continued for 2 years and I feel that I have some mastery in this and will be able to succeed in this class very much. I am also proficient in Flutter for App Development and I look forward to learning more programming to further enhance my skills. 
</div>

<button id="general-btn" style="background-color: #8BC34A; color: #ffffff; transition: transform 0.2s;" onmouseover="this.style.transform='scale(1.05)'" onmouseout="this.style.transform='scale(1)'">General (CLICK ME!)</button>
<div id="general-text" style="display: none; opacity: 0; transition: opacity 1s;">
  I am a 15 year old student at Del Norte High School in the 10th grade. I am nationally ranked Top 40 in the nation for Volleyball and I also enjoy other physical activities such as badminton and karate! In my free time, I like to learn skills like coding and dancing! https://youtu.be/7CFYaKmLbQA
</div>

<script>
  // Smooth fade-in for coding experience
  document.getElementById("coding-experience-btn").addEventListener("click", function() {
    var textDiv = document.getElementById("coding-experience-text");
    if (textDiv.style.display === "none") {
      textDiv.style.display = "block";
      textDiv.style.opacity = "1";
    } else {
      textDiv.style.opacity = "0";
      setTimeout(function() {
        textDiv.style.display = "none";
      }, 1000);
    }
  });

  // Smooth fade-in for general text
  document.getElementById("general-btn").addEventListener("click", function() {
    var textDiv = document.getElementById("general-text");
    if (textDiv.style.display === "none") {
      textDiv.style.display = "block";
      textDiv.style.opacity = "1";
    } else {
      textDiv.style.opacity = "0";
      setTimeout(function() {
        textDiv.style.display = "none";
      }, 1000);
    }
  });
</script>

<!-- Adding hover effect to the image and centering it -->
<div style="text-align: center;">
  <img src="{{site.baseurl}}/images/IMG_3782.jpeg" width="300" height="350" style="transition: transform 0.3s;" onmouseover="this.style.transform='scale(1.1)'" onmouseout="this.style.transform='scale(1)'">
</div>

<button id="home-btn" style="background-color: #4CAF50; color: #ffffff; transition: transform 0.2s;" onmouseover="this.style.transform='scale(1.05)'" onmouseout="this.style.transform='scale(1)'">Back to Home</button>


<!-- Adding Changing Background Color -->
<script>
  let colors = ["#FFFAF0", "#FFFACD", "#E6E6FA", "#F5FFFA"];
  let currentColor = 0;
  setInterval(function() {
    document.body.style.backgroundColor = colors[currentColor];
    currentColor = (currentColor + 1) % colors.length;
  }, 5000); // Change color every 5 seconds
</script>

<!-- Progress bar at the top -->
<div id="progress-bar" style="position: fixed; top: 0; left: 0; height: 5px; background-color: #4CAF50; width: 0%;"></div>

<script>
  // Progress bar to track page scroll
  window.onscroll = function() {
    var scrollProgress = document.documentElement.scrollTop;
    var totalHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
    var scrollPercentage = (scrollProgress / totalHeight) * 100;
    document.getElementById("progress-bar").style.width = scrollPercentage + "%";
  };
</script>

<script>
  document.getElementById("home-btn").addEventListener("click", function() {
    window.location.href = "{{ site.baseurl }}/";
  });
</script>
