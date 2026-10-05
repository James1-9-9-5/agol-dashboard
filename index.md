---
layout: default
title: Hartley Bay Maintenance Management
---
<div id="hb-dashboard">
<style>
  /* ---------- Palette (edit these to match exact logo values) ---------- */
  #hb-dashboard {
    --hb-ink: #1A1A1A;
    --hb-card: #F5F2EE;
    --hb-red: #C8102E;
    --hb-red-dark: #A00D25;
    --hb-muted: #5A5A5A;
    --hb-line: #DDD7CF;
  }

  /* ---------- Shared bits ---------- */
  #hb-dashboard svg.icon {
    fill: none;
    stroke: currentColor;
    stroke-width: 2;
    stroke-linecap: round;
    stroke-linejoin: round;
  }

  /* ---------- Report a Problem (wide card) ---------- */
  #hb-dashboard .report-card {
    display: flex;
    align-items: center;
    gap: 24px;
    width: 100%;
    max-width: 1020px;
    margin: 40px auto 0;
    padding: 26px 32px;
    box-sizing: border-box;
    border: 4px solid #ffffff;
    border-radius: 10px;
    background: var(--hb-red);
    color: #ffffff;
    box-shadow: 0 6px 18px rgba(0,0,0,0.35);
    cursor: pointer;
    text-align: left;
    font: inherit;
    transition: background 0.15s ease, box-shadow 0.15s ease;
  }
  #hb-dashboard .report-card:hover {
    background: var(--hb-red-dark);
    box-shadow: 0 8px 22px rgba(0,0,0,0.45);
  }
  #hb-dashboard .report-card:focus-visible {
    outline: 4px solid #ffffff;
    outline-offset: 3px;
  }
  #hb-dashboard .report-icon {
    flex: 0 0 auto;
    width: 64px;
    height: 64px;
  }
  #hb-dashboard .report-text {
    flex: 1 1 auto;
  }
  #hb-dashboard .report-title {
    display: block;
    font-size: 1.7rem;
    font-weight: 700;
    line-height: 1.2;
    margin: 0 0 4px;
  }
  #hb-dashboard .report-desc {
    display: block;
    font-size: 1.05rem;
    line-height: 1.4;
    opacity: 0.95;
  }
  #hb-dashboard .report-action {
    flex: 0 0 auto;
    padding: 12px 26px;
    border-radius: 999px;
    background: #ffffff;
    color: var(--hb-red);
    font-weight: 700;
    font-size: 1rem;
    white-space: nowrap;
  }

  /* ---------- Management cards ---------- */
  #hb-dashboard .dash-grid {
    display: flex;
    flex-wrap: nowrap;
    gap: 20px;
    margin-top: 18px;
    justify-content: center;
    align-items: stretch;
  }
  #hb-dashboard .dash-card {
    display: flex !important;
    flex-direction: column !important;
    flex: 1 1 240px;
    max-width: 320px;
    min-width: 220px;
    color: var(--hb-ink);
    border: 4px solid #ffffff;
    border-top: 0;
    border-radius: 10px;
    overflow: hidden !important;
    background: var(--hb-card);
    box-shadow: 0 4px 12px rgba(0,0,0,0.25);
    transition: box-shadow 0.15s ease, transform 0.15s ease;
    position: relative;
  }
  #hb-dashboard .dash-card::before {
    content: "";
    display: block;
    height: 8px;
    background: var(--hb-red);
    flex: 0 0 auto;
  }
  #hb-dashboard .dash-card:hover {
    box-shadow: 0 8px 20px rgba(0,0,0,0.35);
    transform: translateY(-3px);
  }

  #hb-dashboard .dash-link {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 6px;
    padding: 28px 18px 22px;
    cursor: pointer;
    flex: 1 1 auto;
  }
  #hb-dashboard .dash-link:focus-visible {
    outline: 3px solid var(--hb-red);
    outline-offset: -3px;
  }
  #hb-dashboard .dash-icon {
    width: 56px;
    height: 56px;
    color: var(--hb-red);
    margin-bottom: 6px;
  }

  /* Icon with small topic badge */
  #hb-dashboard .icon-wrap {
    position: relative;
    width: 56px;
    height: 56px;
    margin-bottom: 6px;
  }
  #hb-dashboard .icon-wrap .dash-icon { margin: 0; }
  #hb-dashboard .icon-badge {
    position: absolute;
    right: -14px;
    bottom: -6px;
    width: 26px;
    height: 26px;
    padding: 4px;
    box-sizing: border-box;
    border-radius: 50%;
    background: var(--hb-red);
    color: #ffffff;
    border: 2px solid var(--hb-card);
  }

  #hb-dashboard .dash-title {
    margin: 0 !important;
    padding: 0 !important;
    font-weight: 700 !important;
    font-size: 1.2rem !important;
    line-height: 1.25;
    color: var(--hb-ink) !important;
    background: none !important;
  }
  #hb-dashboard .dash-desc {
    margin: 0 !important;
    font-size: 0.92rem;
    line-height: 1.4;
    color: var(--hb-muted);
  }

  /* Lock badge (top left) */
  #hb-dashboard .lock-badge {
    position: absolute;
    top: 18px;
    left: 10px;
    width: 18px;
    height: 18px;
    color: var(--hb-muted);
    z-index: 3;
  }

  /* Toggle row */
  #hb-dashboard .toggle-row-wrap {
    padding: 12px 18px 14px !important;
    margin: 0 !important;
    background: #ffffff !important;
    color: var(--hb-ink) !important;
    border-top: 1px solid var(--hb-line);
  }
  #hb-dashboard .toggle-row {
    display: flex !important;
    align-items: center;
    justify-content: center;
    gap: 8px;
  }
  #hb-dashboard .arrow-btn {
    background: transparent !important;
    border: none !important;
    box-shadow: none !important;
    color: var(--hb-ink);
    width: auto !important;
    height: auto !important;
    display: inline-flex !important;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    padding: 8px !important;
    margin: 0 !important;
    transition: opacity 0.15s ease;
  }
  #hb-dashboard .arrow-btn:hover { opacity: 0.55; }
  #hb-dashboard .arrow-btn:focus-visible {
    outline: 2px solid var(--hb-red);
    border-radius: 4px;
  }
  #hb-dashboard .arrow-btn svg {
    width: 12px;
    height: 12px;
    display: block;
  }
  /* Mode label is kept for screen readers only (the card title already names the view) */
  #hb-dashboard .toggle-mode {
    position: absolute;
    width: 1px;
    height: 1px;
    margin: -1px;
    padding: 0;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
  }
  #hb-dashboard .toggle-dots {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 4px;
    margin: 0;
  }
  #hb-dashboard .toggle-dots .dot {
    width: 8px;
    height: 8px;
    box-sizing: content-box;
    padding: 3px;
    background-clip: content-box;
    border-radius: 50%;
    background-color: var(--hb-ink);
    opacity: 0.3;
    cursor: pointer;
    transition: opacity 0.15s ease, transform 0.15s ease;
  }
  #hb-dashboard .toggle-dots .dot:hover { opacity: 0.6; }
  #hb-dashboard .toggle-dots .dot.active {
    opacity: 1;
    background-color: var(--hb-red);
    transform: scale(1.25);
  }

  /* Info button + popover */
  #hb-dashboard .info-btn {
    position: absolute;
    top: 16px;
    right: 8px;
    width: 26px;
    height: 26px;
    border-radius: 50%;
    background: var(--hb-ink);
    color: #ffffff;
    border: 2px solid #ffffff;
    font-size: 0.85rem;
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
    background: var(--hb-red);
  }
  #hb-dashboard .info-popover {
    position: absolute;
    top: 48px;
    right: 8px;
    width: 210px;
    max-width: calc(100% - 16px);
    background: rgba(23, 23, 23, 0.96);
    color: #ffffff;
    font-size: 0.85rem;
    line-height: 1.4;
    padding: 10px 12px;
    border-radius: 8px;
    z-index: 5;
    text-align: left;
    box-shadow: 0 4px 10px rgba(0,0,0,0.35);
    display: none;
  }
  #hb-dashboard .info-popover.open { display: block; }

  /* ---------- Footer ---------- */
  #hb-dashboard .page-footer {
    margin-top: 3rem;
    padding-top: 1.5rem;
    text-align: center;
    display: flex;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
  }
  #hb-dashboard .footer-pill {
    display: inline-block !important;
    padding: 8px 20px !important;
    border-radius: 999px !important;
    background-color: #171717 !important;
    color: #ffffff !important;
    font-size: 0.85rem !important;
    line-height: 1.4 !important;
    border: none !important;
    margin: 0 !important;
  }

  /* ---------- Report / contact modal ---------- */
  #hb-dashboard .contact-modal-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.6);
    z-index: 1000;
    align-items: center;
    justify-content: center;
    padding: 20px;
  }
  #hb-dashboard .contact-modal-overlay.open { display: flex; }
  #hb-dashboard .contact-modal {
    position: relative;
    width: 100%;
    max-width: 400px;
    background: #171717;
    color: #ffffff;
    border-radius: 10px;
    padding: 24px 22px 22px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.4);
    border-top: 6px solid var(--hb-red);
  }
  #hb-dashboard .contact-modal h3 {
    margin: 0 0 6px;
    font-size: 1.2rem;
    font-weight: 700;
    text-align: center;
    color: #ffffff;
  }
  #hb-dashboard .contact-modal .modal-sub {
    margin: 0 0 16px;
    font-size: 0.88rem;
    text-align: center;
    opacity: 0.8;
  }
  #hb-dashboard .contact-modal-close {
    position: absolute;
    top: 12px;
    right: 12px;
    background: transparent;
    border: none;
    color: #ffffff;
    font-size: 1.4rem;
    line-height: 1;
    cursor: pointer;
    padding: 4px;
    opacity: 0.75;
  }
  #hb-dashboard .contact-modal-close:hover { opacity: 1; }
  #hb-dashboard .contact-modal form {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
  #hb-dashboard .contact-modal label {
    font-size: 0.85rem;
    font-weight: 500;
    opacity: 0.9;
    margin-bottom: -6px;
  }
  #hb-dashboard .contact-modal input,
  #hb-dashboard .contact-modal textarea {
    width: 100%;
    box-sizing: border-box;
    padding: 9px 11px;
    border-radius: 6px;
    border: 1px solid rgba(255,255,255,0.25);
    background: #232323;
    color: #ffffff;
    font: inherit;
    font-size: 0.9rem;
    resize: vertical;
  }
  #hb-dashboard .contact-modal input:focus,
  #hb-dashboard .contact-modal textarea:focus {
    outline: none;
    border-color: #ffffff;
  }
  #hb-dashboard .contact-submit-btn {
    margin-top: 4px;
    padding: 11px 16px;
    border-radius: 999px;
    border: none;
    background: var(--hb-red);
    color: #ffffff;
    font-weight: 700;
    font-size: 0.95rem;
    cursor: pointer;
    transition: background 0.15s ease;
  }
  #hb-dashboard .contact-submit-btn:hover { background: var(--hb-red-dark); }
  #hb-dashboard .contact-submit-btn:disabled { opacity: 0.6; cursor: default; }
  #hb-dashboard .contact-status-msg {
    margin: 4px 0 0;
    font-size: 0.85rem;
    text-align: center;
    min-height: 1em;
  }
  #hb-dashboard .contact-status-msg.success { color: #6fd68a; }
  #hb-dashboard .contact-status-msg.error { color: #ff8080; }

  /* ---------- Responsive ---------- */
  @media screen and (max-width: 900px) {
    #hb-dashboard .dash-grid { flex-wrap: wrap; }
    #hb-dashboard .dash-card { flex: 1 1 240px; max-width: 320px; }
  }
  @media screen and (max-width: 700px) {
    #hb-dashboard .report-card {
      flex-direction: column;
      text-align: center;
      padding: 24px 20px;
      gap: 14px;
    }
    #hb-dashboard .report-title { font-size: 1.45rem; }
    #hb-dashboard .report-action { width: 100%; box-sizing: border-box; text-align: center; }
  }
  @media screen and (max-width: 600px) {
    #hb-dashboard .dash-card { width: 100%; max-width: 320px; }
    #hb-dashboard .dash-grid { gap: 20px; }
  }
  @media (prefers-reduced-motion: reduce) {
    #hb-dashboard * { transition: none !important; }
  }
</style>

<!-- REPORT A PROBLEM (everyone) -->
<button class="report-card" type="button" id="hb-report-btn">
  <svg class="icon report-icon" viewBox="0 0 24 24" aria-hidden="true"><path d="m21.73 18-8-14a2 2 0 0 0-3.48 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3"/><path d="M12 9v4"/><path d="M12 17h.01"/></svg>
  <span class="report-text">
    <span class="report-title">Report a problem</span>
    <span class="report-desc">Something broken or unsafe? Tell the Maintenance Office what's wrong and where.</span>
  </span>
  <span class="report-action">Send a report</span>
</button>

<div class="dash-grid">
  <!-- 1. GENERAL MAINTENANCE CARD -->
  <div class="dash-card toggle-card"
       data-dashboard-url="https://gfnt.maps.arcgis.com/apps/dashboards/c81a853e25e24c2981402f59417701b9"
       data-survey-url="https://arcg.is/1XziXe1"
       data-report-url="https://arcgis.com"
       data-dataset-url="https://gfnt.maps.arcgis.com/home/item.html?id=795135d238ed4ecd8e923ffff93d1884&dataTabView=table#data"
       data-dashboard-desc="Live map and summary charts of all open general maintenance work orders."
       data-survey-desc="Submit a new general maintenance request or work order."
       data-report-desc="Browse submitted general maintenance requests in a table."
       data-dataset-desc="Query the raw general maintenance dataset.">
    <svg class="icon lock-badge" viewBox="0 0 24 24" role="img" aria-label="Password required"><title>Password required</title><rect width="18" height="11" x="3" y="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
    <button class="info-btn" type="button" aria-label="More info" aria-haspopup="true" aria-expanded="false">i</button>
    <div class="info-popover"></div>
    <div class="dash-link" tabindex="0" role="link">
      <svg class="icon dash-icon" viewBox="0 0 24 24" aria-hidden="true"><path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"/></svg>
      <div class="dash-title">General Maintenance</div>
      <p class="dash-desc">Track general maintenance work orders</p>
    </div>
    <div class="toggle-row-wrap">
      <div class="toggle-row">
        <button class="arrow-btn" type="button" data-dir="prev" aria-label="Previous option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="16,2 6,12 16,22"/></svg>
        </button>
        <div class="toggle-dots"></div>
        <button class="arrow-btn" type="button" data-dir="next" aria-label="Next option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="8,2 18,12 8,22"/></svg>
        </button>
        <span class="toggle-mode" aria-live="polite">Dashboard</span>
      </div>
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
    <svg class="icon lock-badge" viewBox="0 0 24 24" role="img" aria-label="Password required"><title>Password required</title><rect width="18" height="11" x="3" y="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
    <button class="info-btn" type="button" aria-label="More info" aria-haspopup="true" aria-expanded="false">i</button>
    <div class="info-popover"></div>
    <div class="dash-link" tabindex="0" role="link">
      <svg class="icon dash-icon" viewBox="0 0 24 24" aria-hidden="true"><path d="M15 21v-8a1 1 0 0 0-1-1h-4a1 1 0 0 0-1 1v8"/><path d="M3 10a2 2 0 0 1 .709-1.528l7-5.999a2 2 0 0 1 2.582 0l7 5.999A2 2 0 0 1 21 10v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/></svg>
      <div class="dash-title">Housing Maintenance</div>
      <p class="dash-desc">Track housing repairs and costs</p>
    </div>
    <div class="toggle-row-wrap">
      <div class="toggle-row">
        <button class="arrow-btn" type="button" data-dir="prev" aria-label="Previous option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="16,2 6,12 16,22"/></svg>
        </button>
        <div class="toggle-dots"></div>
        <button class="arrow-btn" type="button" data-dir="next" aria-label="Next option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="8,2 18,12 8,22"/></svg>
        </button>
        <span class="toggle-mode" aria-live="polite">Dashboard</span>
      </div>
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
    <svg class="icon lock-badge" viewBox="0 0 24 24" role="img" aria-label="Password required"><title>Password required</title><rect width="18" height="11" x="3" y="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
    <button class="info-btn" type="button" aria-label="More info" aria-haspopup="true" aria-expanded="false">i</button>
    <div class="info-popover"></div>
    <div class="dash-link" tabindex="0" role="link">
      <!-- Placeholder icon (life buoy). Swap for one that fits what MERRF covers. -->
      <svg class="icon dash-icon" viewBox="0 0 24 24" aria-hidden="true"><circle cx="6" cy="15" r="4"/><circle cx="18" cy="15" r="4"/><path d="M14 15a2 2 0 0 0-2-2 2 2 0 0 0-2 2"/><path d="M2.5 13 5 7c.7-1.3 1.4-2 3-2"/><path d="M21.5 13 19 7c-.7-1.3-1.5-2-3-2"/></svg>
      <div class="dash-title">MERRF Maintenance</div>
      <p class="dash-desc">Track MERRF maintenance and equipment</p>
    </div>
    <div class="toggle-row-wrap">
      <div class="toggle-row">
        <button class="arrow-btn" type="button" data-dir="prev" aria-label="Previous option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="16,2 6,12 16,22"/></svg>
        </button>
        <div class="toggle-dots"></div>
        <button class="arrow-btn" type="button" data-dir="next" aria-label="Next option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="8,2 18,12 8,22"/></svg>
        </button>
        <span class="toggle-mode" aria-live="polite">Dashboard</span>
      </div>
    </div>
  </div>

  <!-- 4. INVENTORY TRACKER CARD (Inventory / Transactions) -->
  <div class="dash-card toggle-card"
       data-inventory-url="https://gfnt.maps.arcgis.com/apps/dashboards/2c40e298c85b485bba89f43bac6b18ec"
       data-transactions-url="https://gfnt.maps.arcgis.com/apps/dashboards/a0f07e1d734c4806b95ed1f199beadb8"
       data-inventory-desc="View current stock levels for tracked inventory items."
       data-transactions-desc="View the history of inventory check-ins and check-outs.">
    <svg class="icon lock-badge" viewBox="0 0 24 24" role="img" aria-label="Password required"><title>Password required</title><rect width="18" height="11" x="3" y="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
    <button class="info-btn" type="button" aria-label="More info" aria-haspopup="true" aria-expanded="false">i</button>
    <div class="info-popover"></div>
    <div class="dash-link" tabindex="0" role="link">
      <svg class="icon dash-icon" viewBox="0 0 24 24" aria-hidden="true"><path d="M11 21.73a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73z"/><path d="M12 22V12"/><path d="m3.3 7 7.703 4.734a2 2 0 0 0 1.994 0L20.7 7"/><path d="m7.5 4.27 9 5.15"/></svg>
      <div class="dash-title">Inventory Tracker</div>
      <p class="dash-desc">Check stock levels and item history</p>
    </div>
    <div class="toggle-row-wrap">
      <div class="toggle-row">
        <button class="arrow-btn" type="button" data-dir="prev" aria-label="Previous option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="16,2 6,12 16,22"/></svg>
        </button>
        <div class="toggle-dots"></div>
        <button class="arrow-btn" type="button" data-dir="next" aria-label="Next option">
          <svg viewBox="0 0 24 24" fill="currentColor"><polygon points="8,2 18,12 8,22"/></svg>
        </button>
        <span class="toggle-mode" aria-live="polite">Inventory</span>
      </div>
    </div>
  </div>
</div>

<!-- FOOTER -->
<div class="page-footer">
  <span class="footer-pill">&copy; 2026 Gitga'at First Nation</span>
</div>

<div class="contact-modal-overlay" id="hb-contact-overlay">
  <div class="contact-modal" role="dialog" aria-modal="true" aria-labelledby="hb-contact-title">
    <button class="contact-modal-close" type="button" id="hb-contact-close" aria-label="Close">&times;</button>
    <h3 id="hb-contact-title">Report a problem or contact the office</h3>
    <p class="modal-sub">Include where the problem is, so the team can find it.</p>
    <form id="hb-contact-form">
      <label for="hb-contact-name">Name</label>
      <input type="text" id="hb-contact-name" name="name" required>
      <label for="hb-contact-reach">Phone or email (optional)</label>
      <input type="text" id="hb-contact-reach" name="reach">
      <label for="hb-contact-details">What's the problem, and where?</label>
      <textarea id="hb-contact-details" name="details" rows="5" required></textarea>
      <button type="submit" class="contact-submit-btn">Send</button>
    </form>
  </div>
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

    // What each view looks like on the card face (icon, title suffix, short text).
    // The longer data-*-desc text still shows in the "i" popover.
    var VIEWS = {
      dashboard: {
        suffix: 'Dashboard',
        desc: 'View live map and charts',
        icon: '<rect width="7" height="9" x="3" y="3" rx="1"/><rect width="7" height="5" x="14" y="3" rx="1"/><rect width="7" height="9" x="14" y="12" rx="1"/><rect width="7" height="5" x="3" y="16" rx="1"/>'
      },
      survey: {
        suffix: 'Survey',
        desc: 'Submit a new request',
        icon: '<rect width="8" height="4" x="8" y="2" rx="1"/><path d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2"/><path d="m9 14 2 2 4-4"/>'
      },
      report: {
        suffix: 'Report',
        desc: 'Run reports',
        icon: '<path d="M9 3H5a2 2 0 0 0-2 2v4m6-6h10a2 2 0 0 1 2 2v4M9 3v18m0 0h10a2 2 0 0 0 2-2V9M9 21H5a2 2 0 0 1-2-2V9m0 0h18"/>'
      },
      dataset: {
        suffix: 'Dataset',
        desc: 'Query the raw data',
        icon: '<ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M3 5v14a9 3 0 0 0 18 0V5"/><path d="M3 12a9 3 0 0 0 18 0"/>'
      },
      box: {
        suffix: 'Files',
        desc: 'Open supporting files',
        icon: '<path d="M20 20a2 2 0 0 0 2-2V8a2 2 0 0 0-2-2h-7.9a2 2 0 0 1-1.69-.9L9.6 3.9A2 2 0 0 0 7.93 3H4a2 2 0 0 0-2 2v13a2 2 0 0 0 2 2Z"/>'
      },
      inventory: {
        title: 'Inventory Levels',
        desc: 'Check current stock levels',
        icon: null /* uses the card's original box icon */
      },
      transactions: {
        title: 'Inventory Transactions',
        desc: 'See check-ins and check-outs',
        icon: '<path d="M8 3 4 7l4 4"/><path d="M4 7h16"/><path d="m16 21 4-4-4-4"/><path d="M20 17H4"/>'
      }
    };

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

      var link = card.querySelector('.dash-link');
      var infoBtn = card.querySelector('.info-btn');
      var popover = card.querySelector('.info-popover');
      var modeLabel = card.querySelector('.toggle-mode');
      var dotsWrap = card.querySelector('.toggle-dots');
      var arrows = card.querySelectorAll('.arrow-btn');
      var index = 0;

      var titleEl = card.querySelector('.dash-title');
      var descEl = card.querySelector('.dash-desc');
      var iconEl = card.querySelector('.dash-icon');
      var baseTitle = titleEl.textContent;
      var topicIcon = iconEl.innerHTML;

      // Wrap the icon and add a small topic badge (not needed on the Inventory card)
      if (!card.hasAttribute('data-transactions-url')) {
        var wrap = document.createElement('div');
        wrap.className = 'icon-wrap';
        iconEl.parentNode.insertBefore(wrap, iconEl);
        wrap.appendChild(iconEl);
        var badge = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
        badge.setAttribute('class', 'icon icon-badge');
        badge.setAttribute('viewBox', '0 0 24 24');
        badge.setAttribute('aria-hidden', 'true');
        badge.innerHTML = topicIcon;
        wrap.appendChild(badge);
      }

      function currentDesc() {
        return card.getAttribute('data-' + options[index].key + '-desc') || options[index].label;
      }

      function currentUrl() {
        return card.getAttribute('data-' + options[index].key + '-url');
      }

      function render() {
        var opt = options[index];
        var v = VIEWS[opt.key];
        modeLabel.textContent = opt.label;
        titleEl.textContent = v.title || (baseTitle + ' ' + v.suffix);
        descEl.textContent = v.desc;
        iconEl.innerHTML = v.icon || topicIcon;
        if (popover) {
          popover.textContent = currentDesc();
        }
        if (link) {
          link.setAttribute('aria-label', baseTitle + ': open ' + opt.label);
        }
        if (dotsWrap) {
          dotsWrap.querySelectorAll('.dot').forEach(function (d, i) {
            d.classList.toggle('active', i === index);
          });
        }
      }

      // One clickable dot per option.
      if (dotsWrap) {
        options.forEach(function (opt, i) {
          var dot = document.createElement('span');
          dot.className = 'dot' + (i === 0 ? ' active' : '');
          dot.setAttribute('role', 'button');
          dot.setAttribute('tabindex', '0');
          dot.setAttribute('aria-label', 'Go to ' + opt.label);

          dot.addEventListener('click', function (e) {
            e.stopPropagation();
            e.preventDefault();
            index = i;
            render();
          });

          dot.addEventListener('keydown', function (e) {
            if (e.key === 'Enter' || e.key === ' ') {
              e.stopPropagation();
              e.preventDefault();
              index = i;
              render();
            }
          });

          dotsWrap.appendChild(dot);
        });
      }

      render();

      function navigate(targetUrl, newTab) {
        if (!targetUrl || targetUrl === '#') return;
        if (newTab) {
          window.open(targetUrl, '_blank');
        } else {
          window.location.href = targetUrl;
        }
      }

      if (link) {
        link.addEventListener('mousedown', function (e) {
          if (e.button === 1) e.preventDefault();
        });

        link.addEventListener('click', function (e) {
          navigate(currentUrl(), e.ctrlKey || e.metaKey);
        });

        link.addEventListener('auxclick', function (e) {
          if (e.button === 1) {
            e.preventDefault();
            navigate(currentUrl(), true);
          }
        });

        link.addEventListener('keydown', function (e) {
          if (e.key === 'Enter' || e.key === ' ') {
            e.preventDefault();
            navigate(currentUrl(), e.ctrlKey || e.metaKey);
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
<script>
  // Report / contact modal (separate script so a card error can never block it)
  (function () {
    var reportBtn = document.getElementById('hb-report-btn');
    var overlay = document.getElementById('hb-contact-overlay');
    var closeBtn = document.getElementById('hb-contact-close');
    var form = document.getElementById('hb-contact-form');
    var nameInput = document.getElementById('hb-contact-name');
    var reachInput = document.getElementById('hb-contact-reach');
    var detailsInput = document.getElementById('hb-contact-details');

    if (!reportBtn || !overlay || !form) return;

    function openModal() {
      overlay.classList.add('open');
      nameInput.focus();
    }

    function closeModal() {
      overlay.classList.remove('open');
      form.reset();
      var msg = form.querySelector('.contact-status-msg');
      if (msg) {
        msg.textContent = '';
        msg.className = 'contact-status-msg';
      }
    }

    [reportBtn].forEach(function (btn) {
      if (!btn) return;
      btn.addEventListener('click', function (e) {
        e.stopPropagation();
        openModal();
      });
    });

    closeBtn.addEventListener('click', function (e) {
      e.stopPropagation();
      closeModal();
    });

    overlay.addEventListener('click', function (e) {
      if (e.target === overlay) closeModal();
    });

    document.addEventListener('keydown', function (e) {
      if (e.key === 'Escape' && overlay.classList.contains('open')) closeModal();
    });

    form.addEventListener('click', function (e) {
      e.stopPropagation();
    });

    var FORMSPREE_ENDPOINT = 'https://formspree.io/f/mqpabgla';
    var submitBtn = form.querySelector('.contact-submit-btn');
    var statusMsg = document.createElement('p');
    statusMsg.className = 'contact-status-msg';
    form.appendChild(statusMsg);

    form.addEventListener('submit', function (e) {
      e.preventDefault();
      var name = nameInput.value.trim();
      var reach = reachInput.value.trim();
      var details = detailsInput.value.trim();

      submitBtn.disabled = true;
      submitBtn.textContent = 'Sending...';
      statusMsg.textContent = '';
      statusMsg.className = 'contact-status-msg';

      fetch(FORMSPREE_ENDPOINT, {
        method: 'POST',
        headers: { 'Accept': 'application/json' },
        body: new URLSearchParams({
          name: name,
          reach: reach,
          message: details,
          _subject: 'Website report from ' + name
        })
      })
        .then(function (response) {
          if (response.ok) {
            statusMsg.textContent = 'Message sent. Thank you!';
            statusMsg.classList.add('success');
            form.reset();
            setTimeout(closeModal, 1500);
          } else {
            statusMsg.textContent = 'Something went wrong. Please try again.';
            statusMsg.classList.add('error');
          }
        })
        .catch(function () {
          statusMsg.textContent = 'Something went wrong. Please try again.';
          statusMsg.classList.add('error');
        })
        .finally(function () {
          submitBtn.disabled = false;
          submitBtn.textContent = 'Send';
        });
    });
  })();
</script>
</div>
