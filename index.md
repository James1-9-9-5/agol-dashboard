---
layout: default
title: Hartley Bay Maintenance Management
---
<div id="hb-dashboard">
<style>
  #hb-dashboard .dash-grid {
    display: flex;
    flex-wrap: nowrap;
    gap: 20px;
    margin-top: 40px;
    justify-content: center;
    align-items: stretch;
  }
  #hb-dashboard .dash-card {
    display: flex !important;
    flex-direction: column !important;
    flex: 1 1 260px;
    max-width: 320px;
    min-width: 240px;
    text-decoration: none;
    color: inherit;
    border: 4px solid #ffffff;
    border-radius: 10px;
    overflow: hidden !important;
    background: #fff;
    box-shadow: 0 4px 12px rgba(0,0,0,0.25);
    transition: box-shadow 0.15s ease, transform 0.15s ease;
    opacity: 0;
    animation: fadeInUp 0.4s ease forwards;
    position: relative;
  }
  #hb-dashboard .dash-card:nth-child(1) { animation-delay: 0.05s; }
  #hb-dashboard .dash-card:nth-child(2) { animation-delay: 0.15s; }
  #hb-dashboard .dash-card:nth-child(3) { animation-delay: 0.25s; }
  #hb-dashboard .dash-card:nth-child(4) { animation-delay: 0.35s; }
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
  #hb-dashboard .dash-card:hover {
    box-shadow: 0 8px 20px rgba(0,0,0,0.35);
    transform: translateY(-3px) scale(1.02) !important;
  }
  #hb-dashboard .dash-title {
    padding: 14px 18px !important;
    font-weight: 600 !important;
    font-size: 1.05rem !important;
    background-color: #171717 !important;
    color: #ffffff !important;
    text-align: center !important;
    margin: 0 !important;
    position: relative;
    z-index: 2;
    min-height: 58px;
    display: flex !important;
    align-items: center;
    justify-content: center;
    line-height: 1.25;
  }

  /* Header Color Adjustments */
  #hb-dashboard .dash-title.housing-header {
    background-color: #ffffff !important;
    color: #000000 !important;
  }
  #hb-dashboard .dash-title.merrf-header {
    background-color: #DE353E !important;
    color: #ffffff !important;
  }
  #hb-dashboard .dash-title.inventory-header {
    background-color: #d9d9d9 !important;
    color: #000000 !important;
  }

  #hb-dashboard .dash-thumb {
    height: 150px !important;
    width: 100% !important;
    display: flex !important;
    align-items: center;
    justify-content: center;
    color: #ffffff;
    background-color: #2d3748;
    cursor: pointer;
    overflow: hidden !important;
    position: relative;
  }
  #hb-dashboard .dash-thumb:focus-visible {
    outline: 3px solid #ffffff;
    outline-offset: -3px;
  }

  #hb-dashboard .dash-thumb img {
    width: 100% !important;
    height: 100% !important;
    object-fit: cover !important;
    display: block !important;
    opacity: 0;
    margin: 0 !important;
    transition: opacity 0.2s ease;
  }
  #hb-dashboard .dash-thumb img.loaded {
    opacity: 1;
  }

  /* Per-dashboard thumbnail backgrounds */
  #hb-dashboard .dash-thumb.general { background-color: #666666; }
  #hb-dashboard .dash-thumb.housing { background-color: #ffffff; }
  #hb-dashboard .dash-thumb.merrf   { background-color: #DE353E; }
  #hb-dashboard .dash-thumb.inventory { background-color: #d9d9d9; }

  #hb-dashboard .icon-wrap {
    width: 48px;
    height: 48px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2.4rem;
    line-height: 1;
  }

  #hb-dashboard .toggle-row-wrap {
    padding: 12px 18px 14px !important;
    background-color: #171717 !important;
    color: #ffffff !important;
    margin: 0 !important;
  }

  /* Custom Toggle Row Variations */
  #hb-dashboard .toggle-row-wrap.housing-toggle {
    background-color: #ffffff !important;
    color: #000000 !important;
  }
  #hb-dashboard .toggle-row-wrap.housing-toggle .arrow-btn {
    color: #000000 !important;
  }
  #hb-dashboard .toggle-row-wrap.merrf-toggle {
    background-color: #DE353E !important;
    color: #ffffff !important;
  }
  #hb-dashboard .toggle-row-wrap.merrf-toggle .arrow-btn {
    color: #ffffff !important;
  }
  #hb-dashboard .toggle-row-wrap.inventory-toggle {
    background-color: #d9d9d9 !important;
    color: #000000 !important;
  }
  #hb-dashboard .toggle-row-wrap.inventory-toggle .arrow-btn {
    color: #000000 !important;
  }

  #hb-dashboard .toggle-row {
    display: flex !important;
    align-items: center;
    justify-content: center;
    gap: 12px;
  }
  #hb-dashboard .arrow-btn {
    background: transparent !important;
    border: none !important;
    box-shadow: none !important;
    color: inherit;
    width: auto !important;
    height: auto !important;
    display: inline-flex !important;
    align-items: center;
    justify-content: center;
    font-size: 1rem;
    line-height: 1;
    cursor: pointer;
    padding: 4px !important;
    margin: 0 !important;
    transition: opacity 0.15s ease;
  }
  #hb-dashboard .arrow-btn:hover {
    opacity: 0.6;
  }
  #hb-dashboard .arrow-btn svg {
    width: 12px;
    height: 12px;
    display: block;
  }
  #hb-dashboard .toggle-mode {
    font-weight: 500;
    font-size: 0.9rem;
    opacity: 0.85;
    min-width: 70px;
    text-align: center;
  }
  #hb-dashboard .toggle-dots {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 6px;
    margin-top: 8px;
  }
  #hb-dashboard .toggle-dots .dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background-color: currentColor;
    opacity: 0.35;
    transition: opacity 0.15s ease, transform 0.15s ease;
  }
  #hb-dashboard .toggle-dots .dot.active {
    opacity: 1;
    transform: scale(1.4);
  }
  #hb-dashboard .thumb-wrap {
    position: relative;
  }
  #hb-dashboard .info-btn {
    position: absolute;
    top: 6px;
    right: 6px;
    width: 16px;
    height: 16px;
    border-radius: 50%;
    background: rgba(0, 0, 0, 0.55);
    color: #ffffff;
    border: 1.5px solid rgba(255, 255, 255, 0.8);
    font-size: 0.6rem;
    font-weight: 700;
    font-style: italic;
    font-family: Georgia, 'Times New Roman', serif;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    z-index: 5;
    padding: 0;
    line-height: 1;
    transition: background 0.15s ease;
  }
  #hb-dashboard .info-btn:hover,
  #hb-dashboard .info-btn:focus-visible {
    background: rgba(0, 0, 0, 0.85);
  }
  #hb-dashboard .info-popover {
    position: absolute;
    top: 28px;
    right: 6px;
    width: 200px;
    max-width: calc(100% - 12px);
    background: rgba(0, 0, 0, 0.92);
    color: #ffffff;
    font-size: 0.78rem;
    line-height: 1.35;
    padding: 10px 12px;
    border-radius: 8px;
    z-index: 5;
    text-align: left;
    box-shadow: 0 4px 10px rgba(0,0,0,0.35);
    display: none;
  }
  #hb-dashboard .info-popover.open {
    display: block;
  }
  #hb-dashboard .page-footer {
    margin-top: 3rem;
    padding-top: 1.5rem;
    text-align: center;
    display: flex;
    justify-content: center;
  }
  #hb-dashboard .footer-pill {
    display: inline-block !important;
    padding: 8px 20px !important;
    border-radius: 999px !important;
    background-color: #171717 !important;
    color: #ffffff !important;
    font-size: 0.85rem !important;
    opacity: 0.95 !important;
    line-height: 1.4 !important;
    border: none !important;
    margin: 0 !important;
  }
  @media screen and (max-width: 900px) {
    #hb-dashboard .dash-grid {
      flex-wrap: wrap;
    }
    #hb-dashboard .dash-card {
      flex: 1 1 260px;
      max-width: 320px;
    }
  }
  @media screen and (max-width: 600px) {
    #hb-dashboard .dash-card {
      width: 100%;
      max-width: 320px;
    }
    #hb-dashboard .dash-grid {
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
     data-report-img="/assets/images/GM_Report.jpg"
     data-dataset-img="/assets/images/GM_Dataset.jpg"
     data-dashboard-desc="Live map and summary charts of all open general maintenance work orders."
     data-survey-desc="Submit a new general maintenance request or work order."
     data-report-desc="Browse submitted general maintenance requests in a table."
     data-dataset-desc="Query the raw general maintenance dataset.">
    <button class="info-btn" type="button" aria-label="More info" aria-haspopup="true" aria-expanded="false">i</button>
    <div class="info-popover"></div>
    <div class="dash-title">General Maintenance</div>
    <div class="thumb-wrap">
      <div class="dash-thumb general" tabindex="0" role="link">
        <img src="/assets/images/GM_Dashboard.jpg" alt="General Maintenance" width="280" height="150">
      </div>
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
      <div class="toggle-dots"></div>
    </div>
  </div>

  <!-- 2. HOUSING MAINTENANCE CARD -->
  <div class="dash-card toggle-card"
       data-dashboard-url="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971#"
       data-survey-url="https://arcg.is/1XziXe1"
       data-report-url="https://survey123.arcgis.com/surveys/65cbce668ade4efaa3a63b9461ea30f8/data?extent=-129.2872,53.4205,-129.2171,53.4291"
       data-dataset-url="https://gfnt.maps.arcgis.com/home/item.html?id=795135d238ed4ecd8e923ffff93d1884&dataTabView=table#data"
       data-box-url="https://tapestryresearch.app.box.com/folder/346256879414"
       data-dashboard-desc="Live map and summary charts of housing maintenance activity and costs."
       data-survey-desc="Submit a new housing maintenance request."
       data-report-desc="Browse submitted housing maintenance requests in a table."
       data-dataset-desc="Query the raw housing maintenance dataset."
       data-box-desc="Open supporting housing maintenance files and documents in Box.">
    <button class="info-btn" type="button" aria-label="More info" aria-haspopup="true" aria-expanded="false">i</button>
    <div class="info-popover"></div>
    <div class="dash-title housing-header">Housing Maintenance</div>
    <div class="thumb-wrap">
      <div class="dash-thumb housing" tabindex="0" role="link">
        <img src="/assets/images/HM_Dashboard.jpg" alt="Housing Maintenance">
      </div>
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
      <div class="toggle-dots"></div>
    </div>
  </div>

  <!-- 3. MERRF MAINTENANCE CARD -->
  <div class="dash-card toggle-card"
       data-dashboard-url="https://gfnt.maps.arcgis.com/apps/dashboards/0b545005cecf45b8b3a597d2b5150971#"
       data-survey-url="https://arcg.is/1XziXe1"
       data-report-url="https://survey123.arcgis.com/surveys/65cbce668ade4efaa3a63b9461ea30f8/data?extent=-129.2872,53.4205,-129.2171,53.4291"
       data-dataset-url="https://gfnt.maps.arcgis.com/home/item.html?id=795135d238ed4ecd8e923ffff93d1884&dataTabView=table#data"
       data-dashboard-desc="Live map and summary charts of MERRF maintenance activity and equipment status."
       data-survey-desc="Submit a new MERRF maintenance request."
       data-report-desc="Browse submitted MERRF maintenance requests in a table."
       data-dataset-desc="Query the raw MERRF maintenance dataset.">
    <button class="info-btn" type="button" aria-label="More info" aria-haspopup="true" aria-expanded="false">i</button>
    <div class="info-popover"></div>
    <div class="dash-title merrf-header">MERRF Maintenance</div>
    <div class="thumb-wrap">
      <div class="dash-thumb merrf" tabindex="0" role="link">
        <img src="/assets/images/MERRF_Dashboard.jpg" alt="MERRF Maintenance">
      </div>
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
      <div class="toggle-dots"></div>
    </div>
  </div>

  <!-- 4. INVENTORY TRACKER CARD (now toggleable: Inventory / Transactions) -->
  <div class="dash-card toggle-card"
       data-inventory-url="https://gfnt.maps.arcgis.com/apps/dashboards/2c40e298c85b485bba89f43bac6b18ec"
       data-transactions-url="https://gfnt.maps.arcgis.com/apps/dashboards/a0f07e1d734c4806b95ed1f199beadb8"
       data-inventory-img="/assets/images/Inventory.jpg"
       data-transactions-img="/assets/images/Inventory.jpg"
       data-inventory-desc="View current stock levels for tracked inventory items."
       data-transactions-desc="View the history of inventory check-ins and check-outs.">
    <button class="info-btn" type="button" aria-label="More info" aria-haspopup="true" aria-expanded="false">i</button>
    <div class="info-popover"></div>
    <div class="dash-title inventory-header">Inventory Tracker</div>
    <div class="thumb-wrap">
      <div class="dash-thumb inventory" tabindex="0" role="link">
        <img src="/assets/images/Inventory.jpg" alt="Inventory Tracker">
      </div>
    </div>
    <div class="toggle-row-wrap inventory-toggle">
      <div class="toggle-row">
        <button class="arrow-btn" type="button" data-dir="prev" aria-label="Previous option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="16,2 6,12 16,22"/></svg>
        </button>
        <span class="toggle-mode">Inventory</span>
        <button class="arrow-btn" type="button" data-dir="next" aria-label="Next option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="8,2 18,12 8,22"/></svg>
        </button>
      </div>
      <div class="toggle-dots"></div>
    </div>
  </div>
</div>

<div class="page-footer">
  <span class="footer-pill">&copy; 2026 Gitga'at First Nation</span>
</div>

<script>
  (function () {
    var cards = document.querySelectorAll('#hb-dashboard .toggle-card');

    function closeAllPopovers(except) {
      document.querySelectorAll('#hb-dashboard .info-popover.open').forEach(function (p) {
        if (p !== except) {
          p.classList.remove('open');
          var btn = p.previousElementSibling;
          if (btn && btn.classList.contains('info-btn')) {
            btn.setAttribute('aria-expanded', 'false');
          }
        }
      });
    }

    document.addEventListener('click', function () {
      closeAllPopovers();
    });

    document.addEventListener('keydown', function (e) {
      if (e.key === 'Escape') closeAllPopovers();
    });

    cards.forEach(function (card) {
      var options;

      if (card.hasAttribute('data-transactions-url')) {
        options = [
          { key: 'inventory', label: 'Inventory' },
          { key: 'transactions', label: 'Transactions' }
        ];
      } else {
        options = [
          { key: 'dashboard', label: 'Dashboard' },
          { key: 'survey', label: 'Survey' },
          { key: 'report', label: 'Report' },
          { key: 'dataset', label: 'Dataset' }
        ];

        if (card.hasAttribute('data-box-url')) {
          options.push({ key: 'box', label: 'Box' });
        }
      }

      var thumb = card.querySelector('.dash-thumb');
      var thumbImg = card.querySelector('.dash-thumb img');
      var infoBtn = card.querySelector('.info-btn');
      var popover = card.querySelector('.info-popover');
      var modeLabel = card.querySelector('.toggle-mode');
      var dotsWrap = card.querySelector('.toggle-dots');
      var arrows = card.querySelectorAll('.arrow-btn');
      var index = 0;

      function currentDesc() {
        return card.getAttribute('data-' + options[index].key + '-desc') || options[index].label;
      }

      // Build one dot per option, up front.
      if (dotsWrap) {
        options.forEach(function (opt, i) {
          var dot = document.createElement('span');
          dot.className = 'dot' + (i === 0 ? ' active' : '');
          dotsWrap.appendChild(dot);
        });
      }
      if (popover) {
        popover.textContent = currentDesc();
      }

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
          thumbImg.classList.remove('loaded');
          thumbImg.onload = function () { thumbImg.classList.add('loaded'); };
          thumbImg.src = img;
        }
        if (popover) {
          popover.textContent = currentDesc();
        }
        if (dotsWrap) {
          var dots = dotsWrap.querySelectorAll('.dot');
          dots.forEach(function (d, i) {
            d.classList.toggle('active', i === index);
          });
        }
      }

      // Ensure the initial image fades in too
      if (thumbImg) {
        if (thumbImg.complete) {
          thumbImg.classList.add('loaded');
        } else {
          thumbImg.onload = function () { thumbImg.classList.add('loaded'); };
        }
      }

      function navigate(targetUrl, newTab) {
        if (!targetUrl || targetUrl === '#') return;
        if (newTab) {
          window.open(targetUrl, '_blank');
        } else {
          window.location.href = targetUrl;
        }
      }

      if (thumb) {
        thumb.addEventListener('mousedown', function (e) {
          if (e.button === 1) { // middle mouse button
            e.preventDefault();
          }
        });

        thumb.addEventListener('click', function (e) {
          var openInNewTab = e.ctrlKey || e.metaKey; // Ctrl (Win/Linux) or Cmd (Mac)
          navigate(currentUrl(), openInNewTab);
        });

        thumb.addEventListener('auxclick', function (e) {
          if (e.button === 1) { // middle mouse button
            e.preventDefault();
            navigate(currentUrl(), true);
          }
        });

        thumb.addEventListener('keydown', function (e) {
          if (e.key === 'Enter' || e.key === ' ') {
            e.preventDefault();
            var openInNewTab = e.ctrlKey || e.metaKey;
            navigate(currentUrl(), openInNewTab);
          }
        });
      }

      if (infoBtn && popover) {
        infoBtn.addEventListener('click', function (e) {
          e.stopPropagation();
          e.preventDefault();
          var isOpen = popover.classList.contains('open');
          closeAllPopovers(isOpen ? null : popover);
          if (!isOpen) {
            popover.classList.add('open');
            infoBtn.setAttribute('aria-expanded', 'true');
          } else {
            infoBtn.setAttribute('aria-expanded', 'false');
          }
        });

        popover.addEventListener('click', function (e) {
          e.stopPropagation();
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
</div>
