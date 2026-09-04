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
  .dash-card:nth-child(4) { animation-delay: 0.35s; }
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
    box-shadow: 0 8px 20px rgba(0,0,0,0.35);
    transform: translateY(-3px);
  }
  .dash-title {
    padding: 14px 18px;
    font-weight: 600;
    font-size: 1.05rem;
    background-color: #171717;
    color: #ffffff;
    text-align: center;
  }
  
  /* Header Color Adjustments */
  .dash-title.housing-header {
    background-color: #ffffff;
    color: #000000;
  }
  .dash-title.merrf-header {
    background-color: #aa0000;
    color: #ffffff;
  }

    .dash-title.inventory-header {
    background-color: #d9d9d9;
    color: #000000;
  }

  .dash-thumb {
    height: 150px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #ffffff;
    background-color: #2d3748;
    cursor: pointer;
  }
  .dash-thumb:focus-visible {
    outline: 3px solid #ffffff;
    outline-offset: -3px;
  }
  .dash-thumb img {
    width: 100%;
    height: 100%;
    object-fit: contain;
    display: block;
  }
  /* Per-dashboard thumbnail backgrounds */
  .dash-thumb.general { background-color: #000000; }
  .dash-thumb.housing { background-color: #ffffff; }
  .dash-thumb.merrf   { background-color: #aa0000; }
  .dash-thumb.inventory { background-color: #d9d9d9; }

  .icon-wrap {
    width: 48px;
    height: 48px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2.4rem;
    line-height: 1;
  }
  .toggle-row-wrap {
    padding: 12px 18px 14px;
    background-color: #171717;
    color: #ffffff;
  }

  /* Custom Toggle Row Variations */
  .toggle-row-wrap.housing-toggle {
    background-color: #ffffff;
    color: #000000;
  }
  .toggle-row-wrap.housing-toggle .arrow-btn {
    color: #000000;
  }
  .toggle-row-wrap.merrf-toggle {
    background-color: #aa0000;
    color: #ffffff;
  }
  .toggle-row-wrap.merrf-toggle .arrow-btn {
    color: #ffffff;
  }

  .toggle-row {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
  }
  .arrow-btn {
    background: transparent;
    border: none;
    color: #ffffff;
    width: auto;
    height: auto;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1rem;
    line-height: 1;
    cursor: pointer;
    padding: 4px;
    transition: opacity 0.15s ease;
  }
  .arrow-btn:hover {
    opacity: 0.6;
  }
  .arrow-btn svg {
    width: 12px;
    height: 12px;
    display: block;
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
  <!-- 1. GENERAL MAINTENANCE CARD -->
<div class="dash-card toggle-card"
     data-dashboard-url="https://gfnt.maps.arcgis.com/apps/dashboards/c81a853e25e24c2981402f59417701b9"
     data-survey-url="https://arcg.is/1XziXe1"
     data-report-url="https://arcgis.com"
     data-dataset-url="https://gfnt.maps.arcgis.com/home/item.html?id=795135d238ed4ecd8e923ffff93d1884&dataTabView=table#data"
     data-dashboard-img="/assets/images/GM_Dashboard.jpg"
     data-survey-img="/assets/images/GM_Survey.jpg"
     data-report-img="/assets/images/FC.jpg"
     data-dataset-img="/assets/images/GM_Dataset.jpg">
    <div class="dash-title">General Maintenance</div>
    <div class="dash-thumb general" tabindex="0" role="link">
      <img src="/assets/images/BO.jpg" alt="General Maintenance">
    </div>
    <div class="toggle-row-wrap">
      <div class="toggle-row">
        <button class="arrow-btn" type="button" data-dir="prev" aria-label="Previous option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="16,2 6,12 16,22"/></svg>
        </button>
        <span class="toggle-mode">Dashboard</span>
        <button class="arrow-btn" type="button" data-dir="next" aria-label="Next option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="8,2 18,12 8,22"/></svg>
        </button>
      </div>
    </div>
  </div>

  <!-- 2. HOUSING MAINTENANCE CARD -->
  <div class="dash-card toggle-card"
       data-dashboard-url="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971#"
       data-survey-url="https://arcg.is/1XziXe1"
       data-report-url="https://survey123.arcgis.com/surveys/65cbce668ade4efaa3a63b9461ea30f8/data?extent=-129.2872,53.4205,-129.2171,53.4291"
       data-dataset-url="https://gfnt.maps.arcgis.com/home/item.html?id=795135d238ed4ecd8e923ffff93d1884&dataTabView=table#data"
       data-box-url="https://tapestryresearch.app.box.com/folder/346256879414">
    <div class="dash-title housing-header">Housing Maintenance</div>
    <div class="dash-thumb housing" tabindex="0" role="link">
      <img src="/assets/images/House.jpg" alt="Housing Maintenance">
    </div>
    <div class="toggle-row-wrap housing-toggle">
      <div class="toggle-row">
        <button class="arrow-btn" type="button" data-dir="prev" aria-label="Previous option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="16,2 6,12 16,22"/></svg>
        </button>
        <span class="toggle-mode">Dashboard</span>
        <button class="arrow-btn" type="button" data-dir="next" aria-label="Next option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="8,2 18,12 8,22"/></svg>
        </button>
      </div>
    </div>
  </div>

  <!-- 3. MERRF MAINTENANCE CARD -->
  <div class="dash-card toggle-card"
       data-dashboard-url="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971#"
       data-survey-url="https://arcg.is/1XziXe1"
       data-report-url="https://survey123.arcgis.com/surveys/65cbce668ade4efaa3a63b9461ea30f8/data?extent=-129.2872,53.4205,-129.2171,53.4291"
       data-dataset-url="https://gfnt.maps.arcgis.com/home/item.html?id=795135d238ed4ecd8e923ffff93d1884&dataTabView=table#data">
    <div class="dash-title merrf-header">MERRF Maintenance</div>
    <div class="dash-thumb merrf" tabindex="0" role="link">
      <img src="/assets/images/MERRF.jpg" alt="MERRF Maintenance">
    </div>
    <div class="toggle-row-wrap merrf-toggle">
      <div class="toggle-row">
        <button class="arrow-btn" type="button" data-dir="prev" aria-label="Previous option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="16,2 6,12 16,22"/></svg>
        </button>
        <span class="toggle-mode">Dashboard</span>
        <button class="arrow-btn" type="button" data-dir="next" aria-label="Next option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="8,2 18,12 8,22"/></svg>
        </button>
      </div>
    </div>
  </div>

  <!-- 4. INVENTORY TRACKER CARD (no toggle) -->
  <a class="dash-card" href="https://gfnt.maps.arcgis.com/apps/dashboards/2c40e298c85b485bba89f43bac6b18ec">
    <div class="dash-title inventory-header">Inventory Tracker</div>
    <div class="dash-thumb inventory">
      <img src="/assets/images/Warehouse.jpg" alt="Inventory Tracker">
    </div>
  </a>
</div>

<div class="page-footer">
  <span class="footer-pill">&copy; 2026 Gitga'at First Nation</span>
</div>

<script>
  (function () {
    var cards = document.querySelectorAll('.toggle-card');

    cards.forEach(function (card) {
      var options = [
        { key: 'dashboard', label: 'Dashboard' },
        { key: 'survey', label: 'Survey' },
        { key: 'report', label: 'Report' },
        { key: 'dataset', label: 'Dataset' }
      ];

      if (card.hasAttribute('data-box-url')) {
        options.push({ key: 'box', label: 'Box' });
      }

      var thumb = card.querySelector('.dash-thumb');
      var thumbImg = card.querySelector('.dash-thumb img');
      var modeLabel = card.querySelector('.toggle-mode');
      var arrows = card.querySelectorAll('.arrow-btn');
      var index = 0;

      function currentUrl() {
        return card.getAttribute('data-' + options[index].key + '-url');
      }

      function currentImg() {
        return card.getAttribute('data-' + options[index].key + '-img');
      }

      function render() {
        modeLabel.textContent = options[index].label;
        var img = currentImg();
        if (img && thumbImg) {
          thumbImg.src = img;
        }
      }

      if (thumb) {
        thumb.addEventListener('click', function() {
          var targetUrl = currentUrl();
          if (targetUrl && targetUrl !== '#') {
            window.location.href = targetUrl;
          }
        });
        
        thumb.addEventListener('keydown', function(e) {
          if (e.key === 'Enter' || e.key === ' ') {
            e.preventDefault();
            var targetUrl = currentUrl();
            if (targetUrl && targetUrl !== '#') {
              window.location.href = targetUrl;
            }
          }
        });
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
    });
  })();
</script>
