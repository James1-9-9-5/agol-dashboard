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
  
  /* New Header Color Adjustments */
  .dash-title.housing-header {
    background-color: #ffffff;
    color: #000000;
  }
  .dash-title.merrf-header {
    background-color: #aa0000;
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
    object-fit: cover;
    display: block;
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
    color: #000000;
  }
  .toggle-row-wrap.merrf-toggle .arrow-btn {
    color: #000000;
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
  <div class="dash-card toggle-card"
       data-dashboard-url="https://arcgis.com"
       data-survey-url="https://arcg.is"
       data-report-url="https://arcgis.com"
       data-dataset-url="https://arcgis.com">
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
  <div class="dash-card toggle-card"
       data-dashboard-url="https://arcgis.com"
       data-survey-url="https://arcg.is"
       data-report-url="https://arcgis.com"
       data-dataset-url="https://arcgis.com"
       data-box-url="https://box.com">
    <div class="dash-title housing-header">Housing Maintenance</div>
    <div class="dash-thumb housing" tabindex="0" role="link">
      <img src="/assets/images/House.jpg" alt="Housing Maintenance">
    </div>
    <!-- Updated Housing Toggle Wrap -->
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
  <div class="dash-card toggle-card"
       data-dashboard-url="https://arcgis.com"
       data-survey-url="https://arcg.is"
       data-report-url="https://arcgis.com"
       data-dataset-url="https://arcgis.com">
    <div class="dash-title merrf-header">MERRF Maintenance</div>
    <div class="dash-thumb merrf" tabindex="0" role="link">
      <img src="/assets/images/MERRF.jpg" alt="MERRF Maintenance">
    </div>
    <!-- Updated MERRF Toggle Wrap -->
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
</div>
<div class="page-footer">
  <span class="footer-pill">&copy; 2026 Gitga'at First Nation</span>
</div>
<script>
  (function () {
    var options = [
      { key: 'dashboard', label: 'Dashboard' },
      { key: 'survey', label: 'Survey' },
      { key: 'report', label: 'Report' },
      { key: 'dataset', label: 'Dataset' }
    ];
    var cards = document.querySelectorAll('.toggle-card');

    cards.forEach(function (card) {
      var thumb = card.querySelector('.dash-thumb');
      var modeLabel = card.querySelector('.toggle-mode');
      var arrows = card.querySelectorAll('.arrow-btn');
      var index = 0;

      function currentUrl() {
        return card.getAttribute('data-' + options[index].key + '-url');
      }

      function render() {
        modeLabel.textContent = options[index].label;
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
