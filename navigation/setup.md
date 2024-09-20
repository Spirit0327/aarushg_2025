---
layout: page
title: Setup
permalink: /setup/
---

<!-- Gradient background and improved fonts -->
<style>
  body {
    font-family: 'Arial', sans-serif;
    background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
    color: #333;
  }

  h2 {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    color: #2E3A59;
    font-size: 30px;
    border-bottom: 2px solid #4CAF50;
    padding-bottom: 10px;
  }

  .step-container {
    background-color: white;
    padding: 20px;
    margin-bottom: 15px;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .step-container h3 {
    color: #4CAF50;
    font-size: 22px;
    margin-bottom: 10px;
  }

  .step-container p {
    font-size: 16px;
    line-height: 1.6;
  }

  .icon {
    margin-right: 10px;
    vertical-align: middle;
  }

  #home-btn {
    background-color: #4CAF50;
    color: white;
    padding: 10px 20px;
    border-radius: 5px;
    border: none;
    font-size: 16px;
    cursor: pointer;
    transition: transform 0.3s, background-color 0.3s;
  }

  #home-btn:hover {
    background-color: #45A049;
    transform: scale(1.1);
  }
</style>

## Setting up the Development Environment

<div class="step-container">
  <h3><img src="https://img.icons8.com/ios/50/000000/code.png" class="icon">Step 1: Install Visual Studio Code</h3>
  <p>I installed <a href="https://code.visualstudio.com/" target="_blank" style="color: #4CAF50; text-decoration: none;">Visual Studio Code</a>, my code editor for writing and testing code.</p>
</div>

<div class="step-container">
  <h3><img src="https://img.icons8.com/ios/50/000000/terminal.png" class="icon">Step 2: Install Homebrew</h3>
  <p>Next, I installed <a href="https://brew.sh/" target="_blank" style="color: #4CAF50; text-decoration: none;">Homebrew</a>, a package manager that helps manage software installations.</p>
</div>

<div class="step-container">
  <h3><img src="https://img.icons8.com/ios/50/000000/settings.png" class="icon">Step 3: Verify Installations</h3>
  <p>I verified that Python, Ruby, and Jupyter were installed correctly by checking their versions in the terminal.</p>
</div>

<div class="step-container">
  <h3><img src="https://img.icons8.com/ios/50/000000/source-code.png" class="icon">Step 4: Set up Virtual Environment</h3>
  <p>To isolate project dependencies, I created a Python virtual environment using the following commands:</p>
  <pre><code>python3 -m venv myenv
source myenv/bin/activate</code></pre>
</div>

<div class="step-container">
  <h3><img src="https://img.icons8.com/ios/50/000000/github.png" class="icon">Step 5: Clone Project Repository</h3>
  <p>I cloned the project repository from GitHub and set up the project locally using the command:</p>
  <pre><code>git clone https://github.com/yourusername/yourproject.git</code></pre>
</div>


<a id="home-btn" href="{{ site.baseurl }}/">Back to Home</a>

<a href="{{ site.baseurl }}/reflection" target="_blank">
    <button style="padding: 10px 20px; background-color: #4CAF50; color: white; border: none; border-radius: 5px; cursor: pointer;">
        View Reflection
    </button>
</a>