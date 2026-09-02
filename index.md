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
    @media screen and (max-width: 600px) {
    .dash-card {
      width: 100%;
      max-width: 320px;
    }

    .dash-grid {
      gap: 20px;
      margin-top: 24px;
    }
  }
</style>

<div class="dash-grid">

  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/c81a853e25e24c2981402f59417701b9">
    <div class="dash-thumb">&#128736;</div>
    <div class="dash-label">General Maintenance</div>
  </a>

  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971">
    <div class="dash-thumb">
      <svg width="48" height="48" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M3 11L12 3L21 11" stroke="#ffffff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        <path d="M5 9.5V20C5 20.5523 5.44772 21 6 21H9C9.55228 21 10 20.5523 10 20V15C10 14.4477 10.4477 14 11 14H13C13.5523 14 14 14.4477 14 15V20C14 20.5523 14.4477 21 15 21H18C18.5523 21 19 20.5523 19 20V9.5" stroke="#ffffff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>
    <div class="dash-label">Housing Maintenance</div>
  </a>

  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971">
    <div class="dash-thumb">&#128300;&#65038;</div>
    <div class="dash-label">MERRF Maintenance</div>
  </a>

</div>
