---
layout: default
title: Hartley Bay Maintenance Management
---

<style>
  .dash-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 28px;
    margin-top: 40px;
    justify-content: center;
  }

  .dash-card {
    display: block;
    width: 280px;
    text-decoration: none;
    color: inherit;
    border: 4px solid #ffffff;
    border-radius: 10px;
    overflow: hidden;
    background: #fff;
    box-shadow: 0 4px 12px rgba(0,0,0,0.25);
    transition: box-shadow 0.15s ease, transform 0.15s ease;
  }

  .dash-card:hover {
    text-decoration: none;
    box-shadow: 0 8px 20px rgba(0,0,0,0.35);
    transform: translateY(-3px);
  }

  .dash-thumb {
    height: 150px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 3rem;
    color: #ffffff;
    background-color: #2d3748;
  }

  .dash-label {
    padding: 16px 18px;
    font-weight: 600;
    font-size: 1.05rem;
    background-color: #171717;
    color: #ffffff;
    text-align: center;
  }
</style>

<div class="dash-grid">

  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/c81a853e25e24c2981402f59417701b9">
    <div class="dash-thumb">&#128736;</div>
    <div class="dash-label">General Maintenance</div>
  </a>

  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971">
    <div class="dash-thumb">&#127968;</div>
    <div class="dash-label">Housing Maintenance</div>
  </a>

  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971">
    <div class="dash-thumb">&#128300;&#65038;</div>
    <div class="dash-label">MERRF Maintenance</div>
  </a>

</div>
