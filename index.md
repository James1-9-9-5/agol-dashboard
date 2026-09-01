---
layout: default
title: Hartley Bay Maintenance Management
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
    border: 4px solid #000000;
    border-radius: 8px;
    overflow: hidden;
    background: #fff;
    transition: box-shadow 0.15s ease, transform 0.15s ease;
  }
  .dash-card:hover {
    text-decoration: none;
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
  .dash-thumb.two { background-color: #d9d9d9; }
  .dash-thumb.three { background-color: #aa0000; }

  .dash-label {
    padding: 14px 16px;
    font-weight: 600;
    font-size: 1rem;
    background-color: #171717;
    color: #ffffff;
  }
</style>

<div class="dash-grid">

  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/c81a853e25e24c2981402f59417701b9">
    <div class="dash-thumb one">&#128736;</div>
    <div class="dash-label">General Maintenance</div>
  </a>

  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971">
    <div class="dash-thumb two">&#127968;</div>
    <div class="dash-label">Housing Maintenance</div>
  </a>

  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971">
    <div class="dash-thumb three">&#128300;</div>
    <div class="dash-label">MERRF Maintenance</div>
  </a>

</div>
