<script lang="ts">
  import { onMount } from 'svelte';
  let { imageSrc }: { imageSrc: string } = $props();
  const features = [ //TODO: change the images
    {
      id: 1,
      title: 'Carbon Accounting',
      desc: 'Automate your Carbon Accounting (GHG Protocol, Scopes 1, 2, 3) with unmatched resolution for purchased goods and services.',
      image:
        'https://images.unsplash.com/photo-1497366811353-6870744d04b2?auto=format&fit=crop&w=1600&q=80'
    },
    {
      id: 2,
      title: 'Compliance',
      desc: 'Measure and report your emissions to stay compliant with EU and U.S. regulations such as CSRD, DPP, and the NY Fashion Act.',
      image:
        'https://images.unsplash.com/photo-1556761175-b413da4baf72?auto=format&fit=crop&w=1600&q=80'
    },
    {
      id: 3,
      title: 'Product LCA',
      desc: 'Environmental impact measurement for all your products on the SKU level, even with incomplete data.',
      image:
        'https://images.unsplash.com/photo-1523726491678-bf852e717f6a?auto=format&fit=crop&w=1600&q=80'
    },
    {
      id: 4,
      title: 'Decarbonization',
      desc: 'Model product- and catalog-level changes in your supply chain and run what-if scenarios to reduce your environmental footprint.',
      image:
        'https://images.unsplash.com/photo-1473448912268-2022ce9509d8?auto=format&fit=crop&w=1600&q=80'
    }
  ];
  let activeTab = $state(1);
  let progress = $state(0);
  const duration = 5000;
  let interval: ReturnType<typeof setInterval>;
  function startTimer() {
    clearInterval(interval);
    progress = 0;
    const startTime = Date.now();
    interval = setInterval(() => {
      const elapsed = Date.now() - startTime;
      // progress = Math.min((elapsed / duration) * 100, 100);
      const t = Math.min(elapsed / duration, 1);
      const k = 9;
      const eased =
        Math.log(1 + k * t) / Math.log(1 + k);
      progress = eased * 100;
      if (progress >= 100) {
        const currentIndex = features.findIndex(
          (feature) => feature.id === activeTab
        );
        const nextIndex = (currentIndex + 1) % features.length;
        activeTab = features[nextIndex].id;
        startTimer();
      }
    }, 50);
  }
  function selectFeature(id: number) {
    activeTab = id;
    startTimer();
  }
  let activeFeature = $derived(
    features.find((feature) => feature.id === activeTab)
  );
  onMount(() => {
    startTimer();
    return () => {
      clearInterval(interval);
    };
  });
</script>
<section class="showcase-section">
  <!-- ONE IMAGE ONLY -->
  <div class="showcase-image-wrapper">
    <img
      src={activeFeature?.image}
      alt={activeFeature?.title}
      class="showcase-image"
    />
  </div>
  <!-- FEATURES -->
  <div class="features-grid">
    {#each features as feature (feature.id)}
      <button
        type="button"
        class:active={activeTab === feature.id}
        class="feature-card"
        onclick={() => selectFeature(feature.id)}
      >
        <div class="progress-track">
          {#if activeTab === feature.id}
            <div
              class="progress-bar"
              style={`width: ${progress}%`}
            ></div>
          {/if}
        </div>
        <h3 class="feature-title">
          {feature.title}
        </h3>
        <p class="feature-desc">
          {feature.desc}
        </p>
        <span class="feature-link">
          Learn more
          <svg
            viewBox="0 0 16 16"
            width="14"
            height="14"
            fill="none"
            stroke="currentColor"
          >
            <path
              d="M3 8h10M9 4l4 4-4 4"
              stroke-width="1.8"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </span>
      </button>
    {/each}
  </div>
</section>
<style>
  .showcase-section {
    width: 100%;
    min-height: 100vh;
    padding: 72px 32px 90px;
    background: #000;
    color: #fff;
  }
  .showcase-image-wrapper {
    width: 100%;
    max-width: 1200px;
    aspect-ratio: 16 / 7;
    margin: 0 auto 60px;
    overflow: hidden;
    border-radius: 20px;
  }
  .showcase-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }
.features-grid {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 32px;
  align-items: start;
}
.feature-card {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 20px 0 0;
  border: none;
  background: transparent;
  color: #fff;
  text-align: left;
  cursor: pointer;
}
.progress-track {
  width: 100%;
  height: 2px;
  margin-bottom: 24px;
  background: rgba(255, 255, 255, 0.2);
  overflow: hidden;
}
.progress-bar {
  height: 100%;
  background: #fff;
  transition: width 50ms linear;
}
.feature-title {
  margin: 0 0 14px;
  font-size: 18px;
  font-weight: 600;
  line-height: 24px;
  /* Important */
  min-height: 24px;
}
.feature-desc {
  margin: 0;
  color: rgba(255, 255, 255, 0.6);
  font-size: 15px;
  line-height: 24px;
  /* Reserve exactly 4 lines */
  min-height: 96px;
}
.feature-link {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  margin-top: 24px;
  font-size: 14px;
  font-weight: 600;
}
  @media (max-width: 900px) {
    .features-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }
  @media (max-width: 600px) {
    .showcase-section {
      padding: 60px 20px;
    }
    .showcase-image-wrapper {
      height: 350px;
      margin-bottom: 50px;
    }
    .features-grid {
      grid-template-columns: 1fr;
    }
  }
</style>