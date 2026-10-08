 <header class="navbar">
    <div class="nav-left">
      <a href="/" class="brand-logo">
        <img
          src="/images/logos/cariman.svg"
          class="logo-mark"
          alt="carimam"
        />
        <span class="brand-name">carimam</span>
      </a>
    </div>

    <nav class="nav-center">
      <div class="nav-dropdown">
        <span>Features</span>
        <svg class="chevron" viewBox="0 0 16 16" fill="none" stroke="currentColor"><path d="M4 6l4 4 4-4" stroke-width="1.8" stroke-linecap="round"/></svg>
      </div>
      <div class="nav-dropdown">
        <span>Solutions</span>
        <svg class="chevron" viewBox="0 0 16 16" fill="none" stroke="currentColor"><path d="M4 6l4 4 4-4" stroke-width="1.8" stroke-linecap="round"/></svg>
      </div>
      <a href="#pricing" class="nav-link">Pricing</a>
      <a href="#about" class="nav-link">About us</a>
      <a href="#customers" class="nav-link">Customers</a>
      <div class="nav-dropdown">
        <span>Resources</span>
        <svg class="chevron" viewBox="0 0 16 16" fill="none" stroke="currentColor"><path d="M4 6l4 4 4-4" stroke-width="1.8" stroke-linecap="round"/></svg>
      </div>
    </nav>

    <div class="nav-right">
      <button class="search-btn" aria-label="Search">
        <svg viewBox="0 0 24 24" width="16" height="16" fill="none" stroke="currentColor" stroke-width="2">
          <circle cx="11" cy="11" r="8"></circle>
          <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
        </svg>
      </button>
      <button class="btn-demo">Get a demo</button>
    </div>
  </header>


<style>
  .navbar {
    position: relative;
    z-index: 20;
    width: 100%;
    max-width: 1320px;
    height: 76px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 32px;
  }

  .brand-logo {
    display: flex;
    align-items: center;
    gap: 8px;
    text-decoration: none;
    color: #000;
  }

  .logo-mark {
    width: 24px;
    height: 24px;
    color: #000;
  }

  .brand-name {
    font-size: 20px;
    font-weight: 700;
    letter-spacing: -0.5px;
  }

  .nav-center {
    display: flex;
    align-items: center;
    gap: 28px;
  }

  .nav-dropdown, .nav-link {
    font-size: 14px;
    font-weight: 500;
    color: #222;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 4px;
    text-decoration: none;
    transition: color 0.15s ease;
  }

  .nav-dropdown:hover, .nav-link:hover {
    color: #666;
  }

  .chevron {
    width: 12px;
    height: 12px;
  }

  .nav-right {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .search-btn {
    background: transparent;
    border: 1px solid #e0e0e0;
    width: 36px;
    height: 36px;
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    color: #333;
    transition: border-color 0.15s ease;
  }

  .search-btn:hover {
    border-color: #999;
  }

  .btn-demo {
    background-color: #000;
    color: #fff;
    border: none;
    padding: 9px 18px;
    font-size: 13.5px;
    font-weight: 600;
    border-radius: 6px;
    cursor: pointer;
    transition: background-color 0.15s ease;
  }

  .btn-demo:hover {
    background-color: #222;
  }

  @media (max-width: 900px) {
    .nav-center {
      display: none;
    }
  }
</style>