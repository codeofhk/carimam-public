<script lang="ts">
  import { onMount } from 'svelte';
  const steps = [
    {
      id: 1,
      title: 'Connect your data',
      description:
        'We map your digital ecosystem — product mix, operations, regions, and reporting goals. Our onboarding team connects existing systems (ERP, PLM, spreadsheets) to Carimam via secure APIs or upload modules. We also onboard suppliers to input primary data and review results — building a centralised, traceable foundation for decision-making.',
      image:
        'https://images.unsplash.com/photo-1556761175-b413da4baf72?auto=format&fit=crop&w=1400&q=80'
    },
    {
      id: 2,
      title: 'Complete the picture',
      description:
        'We identify missing information across products, suppliers, and operations, then fill data gaps using custom emission factors and quality-scored regional defaults. Suppliers can contribute and validate primary data, giving you a more complete and reliable view of your supply chain impact.',
      image:
        'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?auto=format&fit=crop&w=1400&q=80'
    },
    {
      id: 3,
      title: 'Measure full impact',
      description:
        'Our textile-specific engine measures full impact using GHG Protocol-aligned methods. Calculate product-level LCAs across 16 categories for apparel, footwear, and home goods, with visibility into carbon, water, waste, and other key impact areas.',
      image:
        'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?auto=format&fit=crop&w=1400&q=80'
    },
    {
      id: 4,
      title: 'Build trusted intelligence',
      description:
        'Turn fragmented supplier and product data into reliable, audit-ready intelligence. Detect inconsistencies, score data quality, validate supplier inputs, and continuously improve your footprint calculations. Auto-generate Digital Product Passports for every SKU, ready for e-commerce and consumer QR codes.',
      image:
        'https://images.unsplash.com/photo-1551836022-d5d88e9218df?auto=format&fit=crop&w=1400&q=80'
    },
    {
      id: 5,
      title: 'Simplify disclosure',
      description:
        'Automate data aggregation, assign owners, track tasks and timelines, and generate formatted reports for frameworks including CSRD, GRI, BRSR, CDP, and SBTi. Customise disclosure fields, benchmark performance, track KPIs, and compare year-over-year progress with full auditability.',
      image:
        'https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&w=1400&q=80'
    },
    {
      id: 6,
      title: 'Accelerate decarbonization',
      description:
        'Use scenario modelling to simulate decarbonisation strategies, prioritise high-emitting suppliers, forecast future emissions, and compare pathways by supplier, product, or geography. Estimate ROI, account for regional policies like EU CBAM, and track progress toward SBTi FLAG and net-zero goals.',
      image:
        'https://images.unsplash.com/photo-1473448912268-2022ce9509d8?auto=format&fit=crop&w=1400&q=80'
    }
  ];
  let activeStep = $state(1);
  const duration = 5000;
  let timer: ReturnType<typeof setTimeout>;
  function goToStep(id: number) {
    activeStep = id;
    clearTimeout(timer);
    timer = setTimeout(() => {
      const currentIndex = steps.findIndex(
        (step) => step.id === activeStep
      );
      const nextIndex =
        (currentIndex + 1) % steps.length;
      goToStep(steps[nextIndex].id);
    }, duration);
  }
  onMount(() => {
    goToStep(1);
    return () => {
      clearTimeout(timer);
    };
  });
</script>
<section class="how-it-works">
  <div class="section-container">
    <h2 class="section-title">
      How Carimam works
    </h2>
    <div class="how-it-works-grid">
      <!-- LEFT -->
      <div class="steps-container">
        <div class="steps">
          {#each steps as step (step.id)}
            <button
              type="button"
              class:active={activeStep === step.id}
              class="step"
              onclick={() => goToStep(step.id)}
            >
              <!-- LINE -->
              <div class="step-line">
                <!-- Grey background line -->
                <div class="line-track"></div>
                <!-- Black animated line -->
                <div
                  class="line-progress"
                  class:progress-active={activeStep === step.id}
                ></div>
                <!-- Number -->
                <div class="step-number">
                  {String(step.id).padStart(2, '0')}
                </div>
              </div>
              <!-- CONTENT -->
              <div class="step-content">
                <h3 class="step-title">
                  {step.title}
                </h3>
                {#if activeStep === step.id}
                  <div class="step-description">
                    <p>{step.description}</p>
                  </div>
                {/if}
              </div>
            </button>
          {/each}
        </div>
      </div>
      <!-- RIGHT -->
      <div class="image-container">
        <div class="image-wrapper">
          {#each steps as step (step.id)}
            {#if activeStep === step.id}
              <img
                src={step.image}
                alt={step.title}
                class="step-image"
              />
            {/if}
          {/each}
        </div>
      </div>
    </div>
  </div>
</section>
<style>
  .how-it-works {
    width: 100%;
    height: calc(100vh - 150px);
    min-height: 700px;
    padding: 50px 32px;
    box-sizing: border-box;
    background: #fff;
  }
  .section-container {
    width: 100%;
    max-width: 1200px;
    height: 100%;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
  }
  .section-title {
    flex-shrink: 0;
    margin: 0 0 40px;
    font-size: 48px;
    line-height: 1.1;
    font-weight: 600;
  }
  .how-it-works-grid {
    flex: 1;
    min-height: 0;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 70px;
    align-items: center;
  }
  /* --------------------------------
     LEFT
  -------------------------------- */
  .steps-container {
    position: relative;
    height: 100%;
    min-height: 0;
  }
  .steps {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .step {
    position: relative;
    width: 100%;
    display: grid;
    grid-template-columns: 28px 1fr;
    column-gap: 16px;
    padding: 0 0 30px;
    border: 0;
    background: transparent;
    text-align: left;
    cursor: pointer;
    font: inherit;
  }
  /*
    Each step owns its own line.
    Therefore the line automatically gets
    the exact height of THIS step.
  */
  .step-line {
    position: relative;
    width: 28px;
    height: 100%;
    display: flex;
    justify-content: center;
  }
  /* Grey line */
  .line-track {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 50%;
    width: 2px;
    transform: translateX(-50%);
    background: #e5e5e5;
  }
  /*
    Black line.
    It belongs ONLY to the currently active step.
    Its height is controlled using percentage,
    so there are no pixel calculations.
  */
  .line-progress {
    position: absolute;
    top: 0;
    left: 50%;
    width: 2px;
    height: 0%;
    transform: translateX(-50%);
    background: #111;
    transition:
      height 700ms cubic-bezier(0.22, 1, 0.36, 1);
  }
  .line-progress.progress-active {
    animation: stepProgress 5000ms linear forwards;
  }
  /* Number sits on top of the line */
  .step-number {
    position: relative;
    z-index: 2;
    width: 28px;
    height: 28px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    background: #e5e5e5;
    font-size: 11px;
    font-weight: 600;
    color: #777;
    transition:
      background 200ms ease,
      color 200ms ease;
  }
  .step.active .step-number {
    background: #111;
    color: #fff;
  }
  .step-content {
    min-width: 0;
  }
  .step-title {
    margin: 2px 0 0;
    font-size: 24px;
    line-height: 1.25;
    font-weight: 600;
    color: #999;
    transition: color 200ms ease;
  }
  .step.active .step-title {
    color: #111;
  }
  .step-description {
    margin-top: 16px;
    max-width: 430px;
    color: #555;
    font-size: 16px;
    line-height: 1.75;
    animation: descriptionIn 400ms ease;
  }
  .step-description p {
    margin: 0 0 18px;
  }
  .step-description p:last-child {
    margin-bottom: 0;
  }
  @keyframes descriptionIn {
    from {
      opacity: 0;
      transform: translateY(-5px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  /* --------------------------------
     RIGHT
  -------------------------------- */
  .image-container {
    width: 100%;
  }
  .image-wrapper {
    width: 100%;
    aspect-ratio: 1.15 / 1;
    overflow: hidden;
    border: 1px solid #e5e5e5;
    border-radius: 12px;
    background: #f5f5f5;
  }
  .step-image {
    width: 100%;
    height: 100%;
    display: block;
    object-fit: cover;
    animation: imageIn 500ms ease;
  }
  @keyframes imageIn {
    from {
      opacity: 1;
      transform: scale(1.1);
    }
    to {
      opacity: 1;
      transform: scale(1);
    }
  }
  @keyframes stepProgress {
    from {
        height: 0%;
    }
    to {
        height: 100%;
    }
    }
  /* --------------------------------
     TABLET
  -------------------------------- */
  @media (max-width: 900px) {
    .how-it-works {
      height: auto;
      min-height: 0;
    }
    .how-it-works-grid {
      grid-template-columns: 1fr;
    }
    .image-container {
      order: -1;
    }
    .steps-container {
      height: auto;
    }
    .steps {
      height: auto;
    }
  }
  /* --------------------------------
     MOBILE
  -------------------------------- */
  @media (max-width: 600px) {
    .how-it-works {
      padding: 70px 20px;
    }
    .section-title {
      font-size: 36px;
    }
    .step-title {
      font-size: 20px;
    }
    .step-description {
      font-size: 15px;
    }
  }
</style>