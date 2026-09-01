---
layout: default
title: Jimbo's maintenance
---

<style>
  .dash-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 24px;
    margin-top: 20px;
  }

  .dash-card {
    display: block;
    width: 260px;
    text-decoration: none;
    color: inherit;
    border: 1px solid #d1d5da;
    border-radius: 8px;
    overflow: hidden;
    background: #fff;
    transition: box-shadow 0.15s ease, transform 0.15s ease;
  }

  .dash-card:hover {
    box-shadow: 0 6px 16px rgba(0,0,0,0.15);
    transform: translateY(-2px);
  }

  .dash-thumb {
    height: 140px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2.5rem;
    color: #fff;
  }

  .dash-thumb.one { background: linear-gradient(135deg, #4a5568, #2d3748); }
  .dash-thumb.two { background: linear-gradient(135deg, #2b6cb0, #1a365d); }
  .dash-thumb.three { background-color: #aa0000; }
  .dash-label {
    padding: 14px 16px;
    font-weight: 600;
    font-size: 1rem;
  }
</style>
Select a dashboard below to open it. You'll be prompted to sign in with your ArcGIS Online account.
<div class="dash-grid">
  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/c81a853e25e24c2981402f59417701b9" target="_blank" rel="noopener">
    <div class="dash-thumb one">&#128295;</div>
    <div class="dash-label">General Maintenance</div>
  </a>
  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971" target="_blank" rel="noopener">
    <div class="dash-thumb two">&#127968;</div>
    <div class="dash-label">Housing Maintenance</div>
  </a>
    <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971" target="_blank" rel="noopener">
    <div class="dash-thumb three">&#128203;</div>
    <div class="dash-label">MERRF Maintenance</div>
  </a>
</div>
