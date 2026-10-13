<template>
  <section id="speeches" class="speech-section">
    <div class="speech-container">
      <p class="section-eyebrow">HAR DU NÅGOT PÅ HJÄRTAT?</p>

      <h2>Tal & överraskningar</h2>

      <p class="speech-intro">
        Vill du hålla tal, bjuda på ett framträdande eller planera en
        överraskning under bröllopsmiddagen? Vad roligt! Vi vill gärna höra vad
        du har i tankarna.
      </p>

      <p class="speech-details">
        Hör av dig till våra toastmasters via mejl och berätta lite om vad du
        planerar. Då kan ni tillsammans se till att allt blir en fin del av
        bröllopsdagen.
      </p>

      <a
        class="speech-email-link"
        href="mailto:aliceochkalle@hotmail.com?subject=Tal%20och%20%C3%B6verraskningar"
      >
        Mejla toastmasters
      </a>

      <p class="speech-email">aliceochkalle@hotmail.com</p>
    </div>
  </section>
</template>

<style scoped>
  .speech-section {
    padding: clamp(80px, 10vw, 150px) 24px;
    background: #f5eff7;
    color: var(--color-lavender);
    text-align: center;
  }

  .speech-container {
    width: min(100%, 680px);
    margin: 0 auto;
  }

  .section-eyebrow {
    margin-bottom: 24px;
    color: var(--color-olive);
    font-size: 0.72rem;
    letter-spacing: 0.2em;
  }

  .speech-section h2 {
    margin: 0 0 28px;
    font-family: var(--font-heading);
    font-size: clamp(2.8rem, 6vw, 5rem);
    font-weight: 400;
    line-height: 1.1;
  }

  .speech-intro,
  .speech-details {
    max-width: 540px;
    margin: 0 auto 20px;
    font-size: 0.95rem;
    line-height: 1.9;
  }

  .speech-details {
    margin-bottom: 36px;
  }

  .speech-email-link {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 24px;
    padding: 17px 28px;
    border: 1px solid var(--color-lavender);
    background: var(--color-lavender);
    color: #fffdf9;
    font-size: 0.75rem;
    letter-spacing: 0.1em;
    text-decoration: none;
    text-transform: uppercase;
    transition:
      background 0.2s,
      color 0.2s;
  }

  .speech-email-link:hover {
    background: transparent;
    color: var(--color-lavender);
  }

  .speech-email {
    margin: 20px 0 0;
    color: var(--color-olive);
    font-size: 0.85rem;
  }

  @media (max-width: 600px) {
    .speech-section h2 {
      font-size: clamp(2.5rem, 10vw, 3.5rem);
    }

    .speech-email-link {
      width: 100%;
    }
  }
</style>
