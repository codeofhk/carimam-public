<script lang="ts">
  import { onMount } from 'svelte';
  const features = [
    {
      id: 1,
      title: 'One product impact foundation',
      description:
        'Ecochain gives sustainability teams a living foundation for product impact data — not a one-off LCA project. Deliver EPDs, support product carbon claims and provide impact data for management, all from one reliable source that stays up to date as regulations, databases and standards evolve.',
       image:
        'https://images.unsplash.com/photo-1556761175-b413da4baf72?auto=format&fit=crop&w=1400&q=80'
    },
    {
      id: 2,
      title: 'Make better product decisions, faster',
      description:
        'Test the impact of design and sourcing decisions before you commit. Model changes to materials, suppliers, product weight or design and quickly see how they affect your product footprint. Ecochain helps teams balance sustainability improvements with cost and ROI.',
      image:
        'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?auto=format&fit=crop&w=1400&q=80'
    },
    {
      id: 3,
      title: 'Product-specific data that wins business',
      description:
        'Give sales and marketing the trustworthy impact data customers and tenders increasingly demand. Get verifiable, product-specific EPDs, PCFs and footprint results based on your actual production processes and suppliers — not generic portfolio estimates.',
      image:
        'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?auto=format&fit=crop&w=1400&q=80'
    },
    {
      id: 4,
      title: 'Scale sustainability without the bottleneck',
      description:
        'Turn product impact into a scalable business capability. Deliver results in weeks instead of months and support large volumes of EPDs with Ecochain’s “verify once, pay once” model. Your sustainability team can move faster while giving every stakeholder the data they need.',
      image:
        'https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&w=1400&q=80'
    }
  ];
  let activeFeature = $state(0);
  onMount(() => {
    const elements = document.querySelectorAll('.feature-trigger');
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            const index = Number(
              (entry.target as HTMLElement).dataset.index
            );
            activeFeature = index;
          }
        });
      },
      {
        threshold: 0.5
      }
    );
    elements.forEach((element) => observer.observe(element));
    return () => observer.disconnect();
  });
</script>
<section class="difference-section">
  <!-- Sticky viewport -->
  <div class="difference-sticky">
    <!-- Top right heading -->
    <div class="difference-heading">
      <h2>How Carimam differs</h2>
    </div>
    <!-- Center content -->
    <div class="feature-display">
      <div class="feature-text">
        <div class="feature-number">
          {String(activeFeature + 1).padStart(2, '0')}
        </div>
        <h3>
          {features[activeFeature].title}
        </h3>
        <p>
          {features[activeFeature].description}
        </p>
      </div>
        <div class="feature-image">
        {#each features as feature, index (index)}
            <img
            class:active={activeFeature === index}
            src={feature.image}
            alt={feature.title}
            />
        {/each}
        </div>
    </div>
  </div>
  <!-- Invisible scroll triggers -->
  <div class="feature-triggers">
    {#each features as feature, index (index)}
      <div
        class="feature-trigger"
        data-index={index}
        aria-hidden="true"
      ></div>
    {/each}
  </div>
</section>
<style>
  .difference-section {
    position: relative;
    width: 100%;
    min-height: 400vh;
    background: #fff;
  }
  /*
   * This stays fixed within the section while
   * the user scrolls through the feature triggers.
   */
  .difference-sticky {
    position: sticky;
    top: 0;
    height: 100vh;
    width: 100%;
    padding: 40px 48px;
    overflow: hidden;
  }
  /* TOP RIGHT */
  .difference-heading {
    position: absolute;
    left: 23%;
    z-index: 2;
  }
  .difference-heading h2 {
    margin: 0;
    font-size: 80px;
    line-height: 1.2;
    font-weight: 600;
    letter-spacing: -0.02em;
    color: #111;
  }
  /*
   * CENTER AREA
   */
  .feature-display {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 80px;
    padding: 120px 10%;
  }
  .feature-text {
    width: min(430px, 40vw);
  }
  .feature-number {
    width: 36px;
    height: 36px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 24px;
    border-radius: 50%;
    background: #eee;
    font-size: 12px;
    color: #111;
  }
  .feature-text h3 {
    margin: 0 0 24px;
    font-size: clamp(32px, 4vw, 56px);
    line-height: 1.05;
    font-weight: 600;
    letter-spacing: -0.04em;
    color: #111;
  }
  .feature-text p {
    margin: 0;
    font-size: 17px;
    line-height: 1.7;
    color: #666;
  }
    .feature-image {
    position: relative;
    width: min(500px, 42vw);
    aspect-ratio: 1 / 0.85;
    overflow: hidden;
    border-radius: 16px;
    background: #f5f5f5;
    }
    .feature-image img {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    display: block;
    object-fit: cover;
    opacity: 0;
    transform: scale(1.02);
    transition:
        opacity 500ms ease,
        transform 500ms ease;
    }
    .feature-image img.active {
    opacity: 1;
    transform: scale(1);
    }
  /*
   * These elements create the scrolling distance.
   * They don't visually appear.
   */
  .feature-triggers {
    position: absolute;
    top: 0;
    left: 0;
    width: 1px;
    height: 100%;
    pointer-events: none;
  }
  .feature-trigger {
    height: 100vh;
    width: 1px;
  }
  /*
   * MOBILE
   */
  @media (max-width: 768px) {
    .difference-section {
      min-height: 400vh;
    }
    .difference-sticky {
      padding: 24px;
    }
    .difference-heading {
      top: 24px;
      right: 24px;
    }
    .difference-heading h2 {
      font-size: 16px;
    }
    .feature-display {
      flex-direction: column;
      justify-content: center;
      gap: 32px;
      padding: 100px 24px 40px;
    }
    .feature-text {
      width: 100%;
    }
    .feature-text h3 {
      font-size: 36px;
    }
    .feature-text p {
      font-size: 15px;
      line-height: 1.6;
    }
    .feature-image {
      width: 100%;
      max-width: 500px;
    }
  }
</style>
