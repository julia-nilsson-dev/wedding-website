<template>
  <section id="accommodation" class="accommodation-section">
    <div class="accommodation-content">
      <p class="section-eyebrow">BOENDE PÅ GOTLAND</p>

      <h2>Stanna lite längre</h2>

      <p class="accommodation-intro">
        Vi hoppas att ni vill göra bröllopet till en hel helg tillsammans med
        oss. Därför finns möjlighet att bo på Gangvidefarm och njuta av Gotland
        i lugn och ro.
      </p>

      <div class="accommodation-details">
        <div class="detail-item">
          <span class="detail-number">01</span>
          <div>
            <h3>Boende på gården</h3>
            <p>
              Vi erbjuder boende på Gangvidefarm i samband med bröllopet. Mer
              information om rum och fördelning kommer närmare inpå.
            </p>
          </div>
        </div>

        <div class="detail-item">
          <span class="detail-number">02</span>
          <div>
            <h3>Datum att hålla koll på</h3>
            <p>
              Vi ses på Gotland den 13–15 augusti. Planera gärna resan i god
              tid!
            </p>
          </div>
        </div>

        <div class="detail-item">
          <span class="detail-number">03</span>
          <div>
            <h3>Resan till Gotland</h3>
            <p>
              Börja gärna planera hur ni tar er hit. Mer praktisk information om
              resor och transporter kommer snart.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .accommodation-section {
    padding: clamp(80px, 12vw, 160px) 24px;
    background: #fffdf9;
    color: var(--color-olive);
  }

  .accommodation-content {
    width: min(100%, 900px);
    margin: 0 auto;
  }

  .section-eyebrow {
    margin-bottom: 24px;
    color: var(--color-lavender);
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    text-align: center;
  }

  .accommodation-section h2 {
    margin: 0 0 24px;
    font-family: var(--font-heading);
    font-size: clamp(3rem, 7vw, 5.5rem);
    font-weight: 400;
    line-height: 1.05;
    text-align: center;
  }

  .accommodation-intro {
    max-width: 580px;
    margin: 0 auto 72px;
    font-size: 1rem;
    line-height: 1.9;
    text-align: center;
  }

  .accommodation-details {
    border-top: 1px solid rgb(86 87 77 / 25%);
  }

  .detail-item {
    display: grid;
    grid-template-columns: 70px 1fr;
    gap: 24px;
    padding: 32px 0;
    border-bottom: 1px solid rgb(86 87 77 / 25%);
  }

  .detail-number {
    padding-top: 5px;
    color: var(--color-lavender);
    font-family: var(--font-heading);
    font-size: 1.5rem;
  }

  .detail-item h3 {
    margin: 0 0 10px;
    font-family: var(--font-heading);
    font-size: 1.8rem;
    font-weight: 500;
  }

  .detail-item p {
    max-width: 620px;
    margin: 0;
    font-size: 0.95rem;
    line-height: 1.8;
  }

  .accommodation-link {
    display: inline-flex;
    align-items: center;
    gap: 14px;
    margin-top: 36px;
    padding-bottom: 8px;
    border-bottom: 1px solid var(--color-olive);
    font-size: 0.78rem;
    letter-spacing: 0.08em;
    text-decoration: none;
    text-transform: uppercase;
  }

  .accommodation-link:hover {
    opacity: 0.65;
  }

  @media (max-width: 600px) {
    .accommodation-intro {
      margin-bottom: 48px;
    }

    .detail-item {
      grid-template-columns: 36px 1fr;
      gap: 14px;
      padding: 26px 0;
    }
  }
</style>
