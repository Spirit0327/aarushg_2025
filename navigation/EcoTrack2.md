---
layout: page
title: EcoTrack Interactive UI
description: A phone-shaped interactive UI for EcoTrack
permalink: /ecotrack2/
---

# EcoTrack Interactive UI 🌱

A sleek phone-shaped interactive interface with a loading bar and launch button.

<div style="display: flex; justify-content: center; align-items: center; height: 100vh; background-color: #121212; font-family: Arial, sans-serif;">
    <div style="width: 300px; height: 600px; background: #1f1f1f; border-radius: 30px; box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5); display: flex; flex-direction: column; justify-content: space-between; align-items: center; padding: 20px;">
        <div style="margin-top: 20px; display: flex; flex-direction: column; align-items: center;">
            <div style="width: 100px; height: 100px; background: linear-gradient(45deg, #00c853, #1de9b6); border-radius: 50%; display: flex; justify-content: center; align-items: center;">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" style="width: 60%; height: 60%;">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 2a10 10 0 100 20 10 10 0 000-20zm0 0v10M12 14l-2-2" />
                </svg>
            </div>
            <h2 style="color: #fff; margin-top: 10px;">EcoTrack</h2>
        </div>
        <div style="width: 80%; height: 20px; background: #333; border-radius: 10px; overflow: hidden; margin-top: 30px; position: relative;">
            <div style="width: 0; height: 100%; background: linear-gradient(90deg, #00c853, #1de9b6); animation: loading 3s infinite;"></div>
        </div>
        <div style="display: flex; justify-content: space-around; margin-top: 20px;">
            <button onclick="window.location.href='http://127.0.0.1:4100/aarushg_2025/ecotrack3/'" style="padding: 10px 20px; font-size: 16px; border: none; border-radius: 5px; background-color: #00c853; color: white; cursor: pointer;">Get Started</button>
            <button onclick="window.location.href='http://127.0.0.1:4100/aarushg_2025/ecotrack4/'" style="padding: 10px 20px; font-size: 16px; border: none; border-radius: 5px; background-color: #007bff; color: white; cursor: pointer;">Learn More</button>
        </div>
    </div>
</div>

<style>
@keyframes loading {
    0% { width: 0; }
    50% { width: 80%; }
    100% { width: 0; }
}
</style>