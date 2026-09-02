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
    opacity: 0;
    animation: fadeInUp 0.4s ease forwards;
  }
  .dash-card:nth-child(1) { animation-delay: 0.05s; }
  .dash-card:nth-child(2) { animation-delay: 0.15s; }
  .dash-card:nth-child(3) { animation-delay: 0.25s; }
  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(12px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  .dash-card:hover {
    text-decoration: none;
    box-shadow: 0 8px 20px rgba(0,0,0,0.35);
    transform: translateY(-3px);
  }
  .dash-card:focus-visible {
    outline: 3px solid #ffffff;
    outline-offset: 3px;
  }
  .dash-thumb {
    height: 150px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #ffffff;
    background-color: #2d3748;
  }
  /* Per-dashboard thumbnail backgrounds */
  .dash-thumb.general { background-color: #000000; }
  .dash-thumb.housing { background-color: #ffffff; }
  .dash-thumb.merrf   { background-color: #aa0000; }

  .icon-wrap {
    width: 48px;
    height: 48px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2.4rem;
    line-height: 1;
  }
  .dash-label {
    padding: 16px 18px;
    font-weight: 600;
    font-size: 1.05rem;
    background-color: #171717;
    color: #ffffff;
    text-align: center;
  }
  /* Toggle card (General Maintenance) */
  .dash-card.toggle-card {
    cursor: pointer;
  }
  .toggle-label {
    padding: 14px 18px 12px;
  }
  .toggle-title {
    font-weight: 600;
    font-size: 1.05rem;
    margin-bottom: 8px;
  }
  .toggle-row {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
  }
  .arrow-btn {
    background: transparent;
    border: 1px solid #ffffff;
    color: #ffffff;
    width: 26px;
    height: 26px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.95rem;
    line-height: 1;
    cursor: pointer;
    padding: 0;
    transition: background 0.15s ease;
  }
  .arrow-btn:hover {
    background: rgba(255,255,255,0.15);
  }
  .toggle-mode {
    font-weight: 500;
    font-size: 0.9rem;
    opacity: 0.85;
    min-width: 70px;
    text-align: center;
  }
  .page-footer {
    margin-top: 3rem;
    padding-top: 1.5rem;
    text-align: center;
  }
  .footer-pill {
    display: inline-block;
    padding: 8px 20px;
    border-radius: 999px;
    background-color: #171717;
    color: #ffffff;
    font-size: 0.85rem;
    opacity: 0.9;
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
  <div class="dash-card toggle-card" id="general-card"
       data-dashboard-url="https://gfnt.maps.arcgis.com/apps/dashboards/c81a853e25e24c2981402f59417701b9"
       data-survey-url="https://arcg.is/1XziXe1">
    <div class="dash-thumb general"><span class="icon-wrap">&#128736;</span></div>
    <div class="dash-label toggle-label">
      <div class="toggle-title">General Maintenance</div>
      <div class="toggle-row">
        <button class="arrow-btn" type="button" data-dir="prev" aria-label="Previous option">&#8249;</button>
        <span class="toggle-mode" id="general-mode">Dashboard</span>
        <button class="arrow-btn" type="button" data-dir="next" aria-label="Next option">&#8250;</button>
      </div>
    </div>
  </div>
  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971">
    <div class="dash-thumb housing">
      <span class="icon-wrap">
        <svg width="40" height="40" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M3 11L12 3L21 11" stroke="#171717" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M5 9.5V20C5 20.5523 5.44772 21 6 21H9C9.55228 21 10 20.5523 10 20V15C10 14.4477 10.4477 14 11 14H13C13.5523 14 14 14.4477 14 15V20C14 20.5523 14.4477 21 15 21H18C18.5523 21 19 20.5523 19 20V9.5" stroke="#171717" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </span>
    </div>
    <div class="dash-label">Housing Maintenance</div>
  </a>
  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971">
    <div class="dash-thumb merrf"><span class="icon-wrap">&#128300;&#65038;</span></div>
    <div class="dash-label">MERRF Maintenance</div>
  </a>
</div>
<div class="page-footer">
  <span class="footer-pill">&copy; 2026 Gitga'at First Nation</span>
</div>
<script>
  (function () {
    var card = document.getElementById('general-card');
    var modeLabel = document.getElementById('general-mode');
    var arrows = card.querySelectorAll('.arrow-btn');
    var options = ['Dashboard', 'Survey'];
    var index = 0; // 0 = Dashboard, 1 = Survey

    function currentUrl() {
      return index === 0
        ? card.getAttribute('data-dashboard-url')
        : card.getAttribute('data-survey-url');
    }

    function render() {
      modeLabel.textContent = options[index];
    }

    arrows.forEach(function (btn) {
      btn.addEventListener('click', function (e) {
        e.stopPropagation();
        e.preventDefault();
        if (btn.getAttribute('data-dir') === 'next') {
          index = (index + 1) % options.length;
        } else {
          index = (index - 1 + options.length) % options.length;
        }
        render();
      });
    });

    card.addEventListener('click', function () {
      window.location.href = currentUrl();
    });

    render();
  })();
</script>
