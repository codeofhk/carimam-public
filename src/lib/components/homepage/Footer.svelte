<script lang="ts">
  const integrations = [
    {
      name: 'SAP',
      logo: '/images/logos/sap.png'
    },
    {
      name: 'Microsoft Dynamics',
      logo: '/images/logos/microsoft-dynamics.png'
    },
    {
      name: 'Oracle NetSuite',
      logo: '/images/logos/netsuite.png'
    },
    {
      name: 'Centric Software',
      logo: '/images/logos/centric.png'
    },
    {
      name: 'Snowflake',
      logo: '/images/logos/snowflake.png'
    },
    {
      name: 'Power BI',
      logo: '/images/logos/power-bi.png'
    },
    {
      name: 'Tableau',
      logo: '/images/logos/tableau.png'
    },
    {
      name: 'Infor',
      logo: '/images/logos/infor.png'
    },
    {
      name: 'Higg Index',
      logo: '/images/logos/higg-index.png'
    },
    {
      name: 'TrusTrace',
      logo: '/images/logos/trustrace.png'
    },
    {
      name: 'Google BigQuery',
      logo: '/images/logos/bigquery.png'
    },
    {
      name: 'Azure',
      logo: '/images/logos/azure.png'
    },
    {
      name: 'Sage',
      logo: '/images/logos/sage.png'
    },
    {
      name: 'PTC FlexPLM',
      logo: '/images/logos/ptc-flexplm.png'
    },
    {
      name: 'Lectra Kubix Link',
      logo: '/images/logos/lectra-kubix-link.png'
    },
    {
      name: 'Made2Flow',
      logo: '/images/logos/made2flow.png'
    },
    {
      name: 'Textile Genesis',
      logo: '/images/logos/textile-genesis.png'
    },
    {
      name: 'Databricks',
      logo: '/images/logos/databricks.png'
    },
    {
      name: 'Looker',
      logo: '/images/logos/looker.png'
    },
    {
      name: 'AWS Redshift',
      logo: '/images/logos/aws-redshift.png'
    }
  ];
  const footerLinks = {
    Platform: [
      'Platform overview',
      'LCA Engine',
      'Interactive platform',
      'Data ingestion',
      'New features',
      'Customer Journey',
      'Onboarding and Services'
    ],
    Resources: [
      'Policy & Regulations hub',
      'CSRD for fashion brands',
      'carimam blog',
      'Carbon footprint of a dress',
      'Carbon footprint of a t-shirt',
      'Guide: LCA in fashion and textile',
      'Guide: Carbon Accounting for fashion'
    ],
    Company: [
      'Pricing',
      'About us',
      'Customers',
      'Legal notice',
      'Privacy Policy',
      'Terms',
      'Careers',
      'Contact us'
    ],
    Solutions: [
      'Product LCA',
      'Carbon Accounting',
      'Sustainability reporting'
    ]
  };
</script>
<!-- TECH STACK -->
<div class="bottom-content">
  <section class="tech-stack">
    <p class="tech-title">100% integrated with your techstack</p>
    <div class="integration-list">
      <div class="integration-track">
        {#each [...integrations, ...integrations] as integration, id (id)}
          <div class="integration" aria-hidden={id >= integrations.length}>
            <img src={integration.logo} alt={integration.name} />
          </div>
        {/each}
      </div>
    </div>
  </section>
  <!-- DEMO CTA -->
  <section class="demo-section">
    <div class="demo-content">
      <h2>
        Book your personalized<br />
        demo today!
      </h2>
      <a href="/demo" class="demo-button">
        Get a demo <span>→</span>
      </a>
    </div>
  </section>
  <!-- FOOTER -->
  <footer class="footer">
    <div class="footer-inner">
      <div class="footer-brand">
        <div class="brand">
            <img
              src="/images/logos/carimam.svg"
              class="logo-mark"
              alt="carimam"
            />
          <span>carimam</span>
        </div>
        <p>Decarbonizing the fashion industry.</p>
      </div>
      <div class="footer-navigation">
        {#each Object.entries(footerLinks) as [category, links]}
          <div class="footer-column">
            <h3>{category}</h3>
            {#each links as link}
              <a href="/">{link}</a>
            {/each}
          </div>
        {/each}
      </div>
    </div>
    <div class="footer-bottom">
      <span>© 2025 carimam, Inc. All rights reserved.</span>
      <div class="social-links">
        <a href="/" aria-label="LinkedIn">in</a>
        <a href="/" aria-label="YouTube">▶</a>
      </div>
    </div>
  </footer>
</div>
<style>
  /* .bottom-content {
    position: relative;
    z-index: 10;

    margin-top: -100vh;
  } */
  .tech-stack {
    width: 100%;
    overflow: hidden;
    background-color: white;
  }
  .tech-title {
    text-align: center;
    font-size: 52px;
  }
  .integration-list {
    width: 100%;
    overflow: hidden;
    position: relative;
    margin: 3%;
    mask-image: linear-gradient(
      to right,
      transparent,
      black 8%,
      black 92%,
      transparent
    );
  }
  .integration-track {
    display: flex;
    width: max-content;
    gap: 48px;
    animation: marquee 35s linear infinite;
  }
  .integration {
    flex: 0 0 auto;
    width: 120px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .integration img {
    max-width: 100%;
    max-height: 40px;
    object-fit: contain;
  }
  @keyframes marquee {
    from {
      transform: translateX(0);
    }
    to {
      transform: translateX(calc(-50% - 24px));
    }
  }
  @media (prefers-reduced-motion: reduce) {
    .integration-track {
      animation: none;
    }
  }
  .demo-section {
    width: 100%;
    min-height: 275px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #c8d8df;
  }
  .demo-content {
    text-align: center;
  }
  .demo-content h2 {
    margin: 0 0 40px;
    font-size: 38px;
    line-height: 1.1;
    font-weight: 600;
    letter-spacing: -0.035em;
    color: #050505;
  }
  .demo-button {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    padding: 12px 18px;
    border-radius: 5px;
    background: #000;
    color: #fff;
    font-size: 12px;
    font-weight: 600;
    text-decoration: none;
    transition:
      transform 200ms ease,
      opacity 200ms ease;
  }
  .demo-button:hover {
    transform: translateY(-2px);
    opacity: 0.85;
  }
  .footer {
    background: #050505;
    color: #fff;
    padding: 55px 56px 25px;
  }
  .footer-inner {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1.2fr 2.8fr;
    gap: 80px;
  }
  .footer-brand {
    padding-top: 5px;
  }
  .brand {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 29px;
    font-weight: 500;
    letter-spacing: -0.04em;
  }
  .logo-mark {
    width: 48px;
    height: 48px;
    filter: invert(1);
    color: #000;
  } 
  .footer-brand p {
    margin: 10px 0 0;
    font-size: 13px;
    color: #fff;
  }
  .footer-navigation {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 30px;
  }
  .footer-column {
    display: flex;
    flex-direction: column;
    gap: 13px;
  }
  .footer-column h3 {
    margin: 0 0 8px;
    font-size: 13px;
    font-weight: 600;
    color: #999;
  }
  .footer-column a {
    color: #fff;
    font-size: 12px;
    line-height: 1.4;
    text-decoration: none;
  }
  .footer-column a:hover {
    opacity: 0.6;
  }
  .footer-bottom {
    max-width: 1200px;
    margin: 55px auto 0;
    padding-top: 25px;
    border-top: 1px solid #444;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 11px;
  }
  .social-links {
    display: flex;
    gap: 16px;
  }
  .social-links a {
    color: #fff;
    text-decoration: none;
    font-weight: 700;
  }
  @media (max-width: 768px) {
    .tech-stack {
      padding: 0 20px;
    }
    .integration-list {
      grid-template-columns: repeat(2, 1fr);
    }
    .integration {
      min-height: 100px;
    }
    .demo-section {
      min-height: 300px;
      padding: 40px 24px;
    }
    .demo-content h2 {
      font-size: 32px;
    }
    .footer {
      padding: 45px 24px 25px;
    }
    .footer-inner {
      grid-template-columns: 1fr;
      gap: 45px;
    }
    .footer-navigation {
      grid-template-columns: repeat(2, 1fr);
      gap: 35px 20px;
    }
    .footer-bottom {
      margin-top: 45px;
    }
  }
</style>