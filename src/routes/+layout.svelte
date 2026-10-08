<script>
  import Navbar from '#lib/components/homepage/Navbar.svelte';
  import BackgroundGrid from '#lib/components/homepage/Background.svelte';
</script>

<div class="app-layout">
  <BackgroundGrid />
  <Navbar />
  
  <main class="main-content">
    <slot />
  </main>
</div>

<style>
  :global(*) {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  :global(body) {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    color: #111827;
    background-color: #fafaf9;
    -webkit-font-smoothing: antialiased;
    overflow-x: hidden;
  }

  .app-layout {
    position: relative;
    width: 100%;
    display: flex;
    flex-direction: column;
  }

  .main-content {
    position: relative;
    z-index: 10;
    width: 100%;
    display: flex;
    flex-direction: column;
  }
</style>
