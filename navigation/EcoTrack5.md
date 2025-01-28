---
layout: page
title: Understand Your Habits
permalink: /ecotrack5/
---

# Let's Understand Your Habits 📱

Help us learn more about your phone usage to provide better recommendations.

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100vh; background-color: #121212; font-family: Arial, sans-serif; color: white; text-align: center;">
    <div style="width: 300px;">
       <h1 style="font-size: 24px; margin-bottom: 20px;">Let's understand your habits</h1>
        
<form>
    <label for="screen_time" style="display: block; text-align: left;">1. What is your daily average screen time?</label>
    <input type="text" id="screen_time" name="screen_time" style="width: 100%; padding: 10px; margin-bottom: 10px; border-radius: 5px; border: none; color: black;">
    
    <label for="charge_usage" style="display: block; text-align: left;">2. Do you use your phone while charging?</label>
    <select id="charge_usage" name="charge_usage" style="width: 100%; padding: 10px; margin-bottom: 10px; border-radius: 5px; border: none; color: black;">
        <option value="yes">Yes</option>
        <option value="no">No</option>
    </select>
    
    <label for="charge_frequency" style="display: block; text-align: left;">3. How often do you charge your phone daily?</label>
    <input type="text" id="charge_frequency" name="charge_frequency" style="width: 100%; padding: 10px; margin-bottom: 10px; border-radius: 5px; border: none; color: black;">
    
    <label for="overnight_charge" style="display: block; text-align: left;">4. Do you charge overnight or only when necessary?</label>
    <select id="overnight_charge" name="overnight_charge" style="width: 100%; padding: 10px; margin-bottom: 10px; border-radius: 5px; border: none; color: black;">
        <option value="overnight">Overnight</option>
        <option value="necessary">Only when necessary</option>
    </select>
    
    <label for="stream_quality" style="display: block; text-align: left;">5. Do you stream videos in high quality or standard quality?</label>
    <select id="stream_quality" name="stream_quality" style="width: 100%; padding: 10px; margin-bottom: 20px; border-radius: 5px; border: none; color: black;">
        <option value="high">High Quality</option>
        <option value="standard">Standard Quality</option>
    </select>
    
    <button type="submit" style="padding: 10px 20px; font-size: 16px; border: none; border-radius: 5px; background-color: #00c853; color: white; cursor: pointer; width: 100%;">Next</button>
</form>