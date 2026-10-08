<script>
  let activeTab = 'Overview';
  let activeSidebarItem = 'Products';
  let showDetails = true;
  let isPlaying = false;

  const tabs = ['Overview', 'Insights', 'Raw data'];

  const sidebarSections = [
    {
      title: null,
      items: [{ name: 'Home', icon: 'home' }]
    },
    {
      title: 'Collect',
      items: [
        { name: 'Materials', icon: 'layers' },
        { name: 'Products', icon: 'box' },
        { name: 'Data rules', icon: 'sliders' },
        { name: 'Corporate', icon: 'building' }
      ]
    },
    {
      title: 'Measure',
      items: [
        { name: 'Trends', icon: 'trending-up' },
        { name: 'Insights', icon: 'lightbulb' }
      ]
    },
    {
      title: 'Reduce',
      items: [
        { name: 'Product Simulator', icon: 'flask' },
        { name: 'Company', icon: 'briefcase' }
      ]
    },
    {
      title: 'Report',
      items: [
        { name: 'CSRD', icon: 'file-text' }
      ]
    }
  ];

  function togglePlay() {
    isPlaying = !isPlaying;
  }
</script>

<main class="hero-section">
  <!-- Hero Copy -->
  <div class="hero-content">
    <h1 class="hero-title">
      Carbon Management Software<br />
      built for apparel and footwear
    </h1>
    <p class="hero-subtitle">
      Measure, report and reduce your emissions, with no manual effort.
    </p>

    <div class="hero-actions">
      <button class="btn btn-dark" onclick={togglePlay}>
        <span>Watch a demo</span>
        <svg viewBox="0 0 24 24" width="14" height="14" fill="currentColor">
          <path d="M8 5v14l11-7z" />
        </svg>
      </button>
      <a href="#how-it-works" class="btn btn-dark">
        <span>How does it work</span>
        <svg viewBox="0 0 24 24" width="15" height="15" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round">
          <line x1="5" y1="12" x2="19" y2="12"></line>
          <polyline points="12 5 19 12 12 19"></polyline>
        </svg>
      </a>
    </div>
  </div>

  <!-- Interactive Dashboard Mockup Card -->
  <div class="mockup-container">
    <div class="mockup-frame">
      <!-- Sidebar -->
      <aside class="mockup-sidebar">
        <div class="sidebar-logo">
          <svg class="mini-logo" viewBox="0 0 28 28" fill="none">
            <circle cx="8" cy="14" r="4.5" stroke="#111" stroke-width="2" />
            <line x1="18" y1="7" x2="18" y2="21" stroke="#111" stroke-width="2" stroke-linecap="round" />
          </svg>
          <span class="mini-title">Carbonfact</span>
        </div>

        {#each sidebarSections as section,id (id)}
          {#if section.title}
            <div class="sidebar-group-title">{section.title}</div>
          {/if}
          <div class="sidebar-group">
            {#each section.items as item,id (id)}
              <button 
                class="sidebar-item" 
                class:active={activeSidebarItem === item.name}
                onclick={() => activeSidebarItem = item.name}
              >
                {#if item.icon === 'home'}
                  <svg viewBox="0 0 24 24" class="icon"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path></svg>
                {:else if item.icon === 'layers'}
                  <svg viewBox="0 0 24 24" class="icon"><polygon points="12 2 2 7 12 12 22 7 12 2"></polygon><polyline points="2 17 12 22 22 17"></polyline><polyline points="2 12 12 17 22 12"></polyline></svg>
                {:else if item.icon === 'box'}
                  <svg viewBox="0 0 24 24" class="icon"><path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"></path><polyline points="3.27 6.96 12 12.01 20.73 6.96"></polyline><line x1="12" y1="22.08" x2="12" y2="12"></line></svg>
                {:else if item.icon === 'sliders'}
                  <svg viewBox="0 0 24 24" class="icon"><line x1="4" y1="21" x2="4" y2="14"></line><line x1="4" y1="10" x2="4" y2="3"></line><line x1="12" y1="21" x2="12" y2="12"></line><line x1="12" y1="8" x2="12" y2="3"></line><line x1="20" y1="21" x2="20" y2="16"></line><line x1="20" y1="12" x2="20" y2="3"></line></svg>
                {:else if item.icon === 'building'}
                  <svg viewBox="0 0 24 24" class="icon"><rect x="4" y="2" width="16" height="20" rx="2" ry="2"></rect><line x1="9" y1="22" x2="9" y2="22.01"></line><line x1="15" y1="22" x2="15" y2="22.01"></line></svg>
                {:else if item.icon === 'trending-up'}
                  <svg viewBox="0 0 24 24" class="icon"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"></polyline><polyline points="17 6 23 6 23 12"></polyline></svg>
                {:else if item.icon === 'lightbulb'}
                  <svg viewBox="0 0 24 24" class="icon"><path d="M9 18h6"></path><path d="M10 22h4"></path><path d="M15.09 14c.18-.98.65-1.74 1.41-2.5A4.65 4.65 0 0 0 18 8 6 6 0 0 0 6 8c0 1 .23 2.23 1.5 3.5.76.76 1.23 1.52 1.41 2.5h6.18z"></path></svg>
                {:else if item.icon === 'flask'}
                  <svg viewBox="0 0 24 24" class="icon"><path d="M10 2v7.527a2 2 0 0 1-.211.896L4.72 20.55a1 1 0 0 0 .9 1.45h12.76a1 1 0 0 0 .9-1.45l-5.069-10.127A2 2 0 0 1 14 9.527V2"></path><line x1="8.5" y1="2" x2="15.5" y2="2"></line></svg>
                {:else if item.icon === 'briefcase'}
                  <svg viewBox="0 0 24 24" class="icon"><rect x="2" y="7" width="20" height="14" rx="2" ry="2"></rect><path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"></path></svg>
                {:else if item.icon === 'file-text'}
                  <svg viewBox="0 0 24 24" class="icon"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path><polyline points="14 2 14 8 20 8"></polyline><line x1="16" y1="13" x2="8" y2="13"></line><line x1="16" y1="17" x2="8" y2="17"></line></svg>
                {/if}
                <span>{item.name}</span>
              </button>
            {/each}
          </div>
        {/each}
      </aside>

      <!-- Main Preview Content Area -->
      <div class="mockup-main">
        <!-- Top Toolbar -->
        <div class="dash-header">
          <button class="back-link">
            <svg viewBox="0 0 16 16" width="12" height="12" fill="none" stroke="currentColor"><path d="M10 12l-4-4 4-4" stroke-width="2" stroke-linecap="round"/></svg>
            <span>Products</span>
          </button>
          <div class="dash-header-actions">
            <div class="dropdown-pill">
              <span>Unit: <strong>Carbon (CO2e)</strong></span>
              <svg viewBox="0 0 16 16" width="10" height="10" stroke="currentColor"><path d="M4 6l4 4 4-4" stroke-width="2" stroke-linecap="round" fill="none"/></svg>
            </div>
            <button class="btn-dark-sm">Simulate changes</button>
          </div>
        </div>

        <!-- Product Identity Bar -->
        <div class="product-banner">
          <div class="product-thumb">
            <!-- Vector T-shirt graphic -->
            <svg viewBox="0 0 100 100" class="shirt-svg">
              <path d="M30,22 L40,30 C45,33 55,33 60,30 L70,22 L88,38 L76,50 L72,44 L72,82 L28,82 L28,44 L24,50 L12,38 Z" fill="#b9c9d6" stroke="#94a3b8" stroke-width="2" />
              <path d="M40,30 C45,35 55,35 60,30" fill="none" stroke="#94a3b8" stroke-width="2" />
            </svg>
          </div>

          <div class="product-info-wrap">
            <div class="product-title-row">
              <h3 class="prod-name">T-shirt</h3>
              <span class="co2-badge">
                <strong>8.2 ± 3.3</strong> kgCO2e
                <span class="status-indicator">
                  <span class="dot-green"></span>
                  <span class="bar-grey"></span>
                </span>
                <svg viewBox="0 0 16 16" width="10" height="10" stroke="currentColor"><path d="M4 6l4 4 4-4" stroke-width="2" stroke-linecap="round" fill="none"/></svg>
              </span>
            </div>

            <div class="product-tags-row">
              <span class="tag-pill">T-Shirt</span>
              <span class="tag-pill">211g</span>
              <span class="tag-pill">10/10 variants collected</span>
            </div>
          </div>

          <div class="variant-select">
            <span>Variant: <strong>Blue</strong></span>
            <svg viewBox="0 0 16 16" width="10" height="10" stroke="currentColor"><path d="M4 6l4 4 4-4" stroke-width="2" stroke-linecap="round" fill="none"/></svg>
          </div>
        </div>

        <!-- Dashboard Navigation Tabs -->
        <div class="dash-tabs">
          {#each tabs as tab, i (i)}
            <button 
              class="dash-tab" 
              class:active={activeTab === tab}
              onclick={() => activeTab = tab}
            >
              {tab}
            </button>
          {/each}
        </div>

        <!-- Making Section -->
        <div class="card-section">
          <div class="card-header">
            <div class="section-badge">1</div>
            <div class="section-title-group">
              <h4>Making</h4>
              <p>Materials and techniques used to make this product</p>
            </div>
            <span class="section-total">4 kgCO2e</span>
          </div>

          <div class="card-body-box">
            <div class="box-top-row">
              <div class="box-title">
                <svg viewBox="0 0 24 24" width="14" height="14" fill="none" stroke="currentColor" stroke-width="2"><polygon points="12 2 2 7 12 12 22 7 12 2"></polygon></svg>
                <strong>Main fabric</strong> <span class="dim">(100% · 211g)</span>
              </div>
              <div class="supplier-tag">
                <span class="red-dot"></span> Siyaram Silk Mills Limited
              </div>
              <span class="box-val">3 kgCO2e</span>
            </div>

            {#if showDetails}
              <div class="breakdown-table">
                <div class="row">
                  <span class="label">Composition</span>
                  <div class="val-group">
                    <span class="sub-pill"><span class="red-dot"></span> Cotton 100%</span>
                  </div>
                  <span class="num">0.5 kgCO2e</span>
                </div>

                <div class="row">
                  <span class="label"></span>
                  <div class="val-group">
                    <span class="sub-pill"><span class="red-dot"></span> Polyester 100%</span>
                  </div>
                  <span class="num">0.12 kgCO2e</span>
                </div>

                <div class="row">
                  <span class="label">Textile formation</span>
                  <span class="chip-badge">Weaving</span>
                  <span class="num">1.5 kgCO2e</span>
                </div>

                <div class="row">
                  <span class="label">Dyeing</span>
                  <span class="chip-badge">Cationic</span>
                  <span class="num">0.75 kgCO2e</span>
                </div>

                <div class="row">
                  <span class="label">Finishing</span>
                  <span class="chip-badge">Not specified</span>
                  <span class="num">0.4 kgCO2e</span>
                </div>
              </div>
            {/if}

            <button class="toggle-details-btn" onclick={() => showDetails = !showDetails}>
              {showDetails ? 'Hide details' : 'Show details'}
            </button>
          </div>
        </div>

        <!-- Assembling Section (Bottom Peek) -->
        <div class="card-section peek">
          <div class="card-header">
            <div class="section-badge">2</div>
            <div class="section-title-group">
              <h4>Assembling</h4>
              <p><span class="red-dot"></span> Siyaram Silk Mills Limited &nbsp;·&nbsp; Loss ratio: 25%</p>
            </div>
            <span class="section-total">5 kgCO2e</span>
          </div>
        </div>
      </div>

      <!-- Center Play Button Overlay -->
      <button class="play-overlay-button" onclick={togglePlay} aria-label="Play video preview">
        <svg viewBox="0 0 24 24" width="24" height="24" fill="white">
          <polygon points="6,3 20,12 6,21" />
        </svg>
      </button>
    </div>
  </div>
</main>

<style>
  .hero-section {
    position: relative;
    z-index: 5;
    width: 100%;
    min-height: 100vh;
    max-width: 1200px;
    margin: 0 auto;
    padding: 36px 24px 80px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .hero-content {
    text-align: center;
    max-width: 860px;
    margin-bottom: 40px;
  }

  .hero-title {
    font-size: 46px;
    line-height: 1.15;
    font-weight: 800;
    color: #0d0f11;
    letter-spacing: -1.2px;
    margin-bottom: 16px;
  }

  .hero-subtitle {
    font-size: 17px;
    color: #52525b;
    font-weight: 400;
    margin-bottom: 26px;
  }

  .hero-actions {
    display: flex;
    justify-content: center;
    gap: 12px;
  }

  .btn {
    border: none;
    outline: none;
    font-size: 13.5px;
    font-weight: 600;
    border-radius: 6px;
    cursor: pointer;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    text-decoration: none;
    padding: 10px 20px;
    transition: background-color 0.15s ease, transform 0.1s ease;
  }

  .btn:active {
    transform: scale(0.98);
  }

  .btn-dark {
    background-color: #000;
    color: #fff;
  }

  .btn-dark:hover {
    background-color: #262626;
  }

  /* Mockup Frame */
  .mockup-container {
    width: 100%;
    max-width: 900px;
    position: relative;
  }

  .mockup-frame {
    position: relative;
    background: #fff;
    border: 1px solid #d4d4d8;
    border-radius: 12px;
    box-shadow: 0 20px 40px -10px rgba(0, 0, 0, 0.08), 0 1px 3px rgba(0, 0, 0, 0.05);
    display: flex;
    overflow: hidden;
    min-height: 520px;
    font-size: 13px;
  }

  /* Mockup Sidebar */
  .mockup-sidebar {
    width: 195px;
    border-right: 1px solid #f0f0f0;
    background: #fafafa;
    padding: 14px 10px;
    display: flex;
    flex-direction: column;
    gap: 8px;
    flex-shrink: 0;
  }

  .sidebar-logo {
    display: flex;
    align-items: center;
    gap: 6px;
    padding: 4px 8px 10px;
  }

  .mini-logo {
    width: 18px;
    height: 18px;
  }

  .mini-title {
    font-size: 14px;
    font-weight: 700;
    letter-spacing: -0.3px;
  }

  .sidebar-group-title {
    font-size: 10.5px;
    font-weight: 600;
    color: #9ca3af;
    padding: 6px 8px 2px;
    letter-spacing: 0.2px;
  }

  .sidebar-group {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .sidebar-item {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 6px 8px;
    border-radius: 6px;
    background: transparent;
    border: none;
    color: #4b5563;
    font-size: 12px;
    font-weight: 500;
    cursor: pointer;
    text-align: left;
    transition: all 0.1s ease;
  }

  .sidebar-item:hover {
    background: #eaeaea;
    color: #000;
  }

  .sidebar-item.active {
    background: #eaeaea;
    color: #111;
    font-weight: 600;
  }

  .sidebar-item .icon {
    width: 14px;
    height: 14px;
    stroke: currentColor;
    stroke-width: 2;
    fill: none;
    flex-shrink: 0;
  }

  /* Mockup Main Panel */
  .mockup-main {
    flex: 1;
    padding: 14px 20px 20px;
    background: #ffffff;
    display: flex;
    flex-direction: column;
    gap: 14px;
  }

  .dash-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .back-link {
    display: inline-flex;
    align-items: center;
    gap: 4px;
    background: none;
    border: none;
    font-size: 11.5px;
    font-weight: 500;
    color: #64748b;
    cursor: pointer;
  }

  .dash-header-actions {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .dropdown-pill {
    font-size: 11px;
    border: 1px solid #e5e7eb;
    padding: 4px 8px;
    border-radius: 4px;
    display: flex;
    align-items: center;
    gap: 6px;
    color: #374151;
    background: #fff;
  }

  .btn-dark-sm {
    background: #27272a;
    color: #fff;
    border: none;
    padding: 5px 10px;
    border-radius: 4px;
    font-size: 11px;
    font-weight: 500;
    cursor: pointer;
  }

  /* Product Banner */
  .product-banner {
    display: flex;
    align-items: center;
    gap: 14px;
  }

  .product-thumb {
    width: 44px;
    height: 44px;
    background: #f1f5f9;
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid #e2e8f0;
  }

  .shirt-svg {
    width: 32px;
    height: 32px;
  }

  .product-info-wrap {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 4px;
  }

  .product-title-row {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .prod-name {
    font-size: 16px;
    font-weight: 700;
    color: #111;
  }

  .co2-badge {
    background: #f3f4f6;
    border: 1px solid #e5e7eb;
    padding: 2px 7px;
    border-radius: 4px;
    font-size: 11px;
    color: #374151;
    display: flex;
    align-items: center;
    gap: 5px;
  }

  .status-indicator {
    display: inline-flex;
    align-items: center;
    gap: 2px;
  }

  .dot-green {
    width: 7px;
    height: 7px;
    background: #10b981;
    border-radius: 50%;
  }

  .bar-grey {
    width: 14px;
    height: 3px;
    background: #cbd5e1;
    border-radius: 2px;
  }

  .product-tags-row {
    display: flex;
    align-items: center;
    gap: 5px;
  }

  .tag-pill {
    background: #f1f5f9;
    color: #475569;
    font-size: 10px;
    font-weight: 600;
    padding: 2px 6px;
    border-radius: 3px;
  }

  .variant-select {
    font-size: 11px;
    border: 1px solid #e2e8f0;
    border-radius: 4px;
    padding: 4px 8px;
    display: flex;
    align-items: center;
    gap: 6px;
    color: #334155;
  }

  /* Tabs */
  .dash-tabs {
    display: flex;
    gap: 18px;
    border-bottom: 1px solid #e5e7eb;
    padding-top: 4px;
  }

  .dash-tab {
    background: none;
    border: none;
    font-size: 12px;
    font-weight: 500;
    color: #6b7280;
    padding-bottom: 6px;
    cursor: pointer;
    position: relative;
  }

  .dash-tab.active {
    color: #111;
    font-weight: 600;
  }

  .dash-tab.active::after {
    content: '';
    position: absolute;
    bottom: -1px;
    left: 0;
    right: 0;
    height: 2px;
    background: #111;
  }

  /* Card Section */
  .card-section {
    border: 1px solid #e5e7eb;
    border-radius: 8px;
    padding: 12px;
    background: #ffffff;
  }

  .card-section.peek {
    opacity: 0.65;
    margin-top: -4px;
  }

  .card-header {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 8px;
  }

  .section-badge {
    width: 20px;
    height: 20px;
    background: #f3f4f6;
    border-radius: 50%;
    font-size: 11px;
    font-weight: 700;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #1f2937;
  }

  .section-title-group h4 {
    font-size: 13px;
    font-weight: 600;
    color: #111827;
  }

  .section-title-group p {
    font-size: 11px;
    color: #6b7280;
  }

  .section-total {
    margin-left: auto;
    font-size: 12px;
    font-weight: 600;
    color: #111827;
  }

  .card-body-box {
    background: #fbfbfb;
    border: 1px solid #f0f0f0;
    border-radius: 6px;
    padding: 10px 12px;
  }

  .box-top-row {
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 11.5px;
    padding-bottom: 8px;
    border-bottom: 1px solid #f1f5f9;
  }

  .box-title {
    display: flex;
    align-items: center;
    gap: 5px;
  }

  .dim {
    color: #64748b;
  }

  .supplier-tag {
    display: inline-flex;
    align-items: center;
    gap: 4px;
    font-size: 10.5px;
    color: #475569;
  }

  .red-dot {
    width: 6px;
    height: 6px;
    background: #ef4444;
    border-radius: 50%;
    display: inline-block;
  }

  .box-val {
    margin-left: auto;
    font-weight: 600;
    font-size: 11.5px;
    color: #111;
  }

  .breakdown-table {
    display: flex;
    flex-direction: column;
    gap: 6px;
    padding: 8px 0;
    font-size: 11px;
  }

  .breakdown-table .row {
    display: grid;
    grid-template-columns: 110px 1fr auto;
    align-items: center;
    gap: 8px;
  }

  .breakdown-table .label {
    color: #6b7280;
  }

  .sub-pill {
    background: #fff;
    border: 1px solid #e5e7eb;
    border-radius: 3px;
    padding: 2px 6px;
    font-size: 10px;
    display: inline-flex;
    align-items: center;
    gap: 4px;
  }

  .chip-badge {
    background: #e2e8f0;
    color: #334155;
    padding: 1px 6px;
    border-radius: 3px;
    font-size: 10.5px;
    justify-self: start;
  }

  .breakdown-table .num {
    background: #f1f5f9;
    padding: 1px 5px;
    border-radius: 3px;
    font-weight: 500;
    color: #475569;
  }

  .toggle-details-btn {
    background: #fff;
    border: 1px solid #d1d5db;
    border-radius: 4px;
    font-size: 10.5px;
    font-weight: 600;
    padding: 3px 8px;
    color: #374151;
    cursor: pointer;
    margin-top: 4px;
  }

  .toggle-details-btn:hover {
    background: #f9fafb;
  }

  /* Play Overlay Button */
  .play-overlay-button {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 66px;
    height: 66px;
    background: #090a0b;
    border: 2px solid rgba(255, 255, 255, 0.15);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.35);
    transition: transform 0.2s cubic-bezier(0.34, 1.56, 0.64, 1), background-color 0.15s ease;
    z-index: 20;
  }

  .play-overlay-button:hover {
    transform: translate(-50%, -50%) scale(1.08);
    background: #18181b;
  }

  .play-overlay-button svg {
    margin-left: 3px;
  }

  @media (max-width: 900px) {
    .hero-title {
      font-size: 32px;
    }

    .mockup-sidebar {
      width: 54px;
      padding: 10px 4px;
    }

    .sidebar-group-title,
    .sidebar-item span,
    .mini-title {
      display: none;
    }

    .sidebar-item {
      justify-content: center;
      padding: 8px;
    }
  }
</style>