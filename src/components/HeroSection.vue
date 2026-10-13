<script setup>
  import heroImage from "../assets/images/hero.jpg";
</script>

<template>
  <section id="home" class="hero">
    <div class="hero-image-container">
      <img
        class="hero-image"
        :src="heroImage"
        alt="Alice och Kalle på Gotland"
      />
    </div>

    <div class="hero-overlay"></div>

    <div class="hero-content">
      <p class="hero-eyebrow">GOTLAND</p>
      <h1 class="hero-title">Alice & Kalle</h1>
      <p class="hero-date">13 — 15 AUGUSTI 2027</p>
    </div>

    <span class="hero-caption">En helg att minnas</span>
  </section>
</template>

<style scoped>
  .hero {
    position: relative;
    display: grid;
    grid-template-areas: "hero";
    place-items: end center;
    overflow: hidden;
    color: var(--color-cream);
    text-align: center;
    background: var(--color-olive);
  }

  .hero-image-container {
    grid-area: hero;
    width: 100%;
    max-height: 98svh;
    overflow: hidden;
  }

  .hero-image {
    display: block;
    width: 100%;
    height: auto;
    max-height: 98svh;
    object-fit: cover;
    object-position: center;
  }

  /* Begränsa sektionens höjd när bilden når maxhöjden */
  @supports (height: 98svh) {
    .hero-image-container {
      height: auto;
    }

    .hero-image {
      width: 100%;
    }
  }

  .hero-overlay {
    grid-area: hero;
    align-self: stretch;
    justify-self: stretch;
    z-index: 1;
    pointer-events: none;
    background: linear-gradient(
      to bottom,
      rgba(40, 42, 35, 0.05) 35%,
      rgba(40, 42, 35, 0.48) 100%
    );
  }

  .hero-content {
    grid-area: hero;
    position: relative;
    z-index: 2;
    width: 100%;
    padding: 40px 24px 5%;
  }

  .hero-eyebrow,
  .hero-date {
    font-size: clamp(0.65rem, 1.2vw, 1rem);
    letter-spacing: 0.22em;
    line-height: 1.8;
  }

  .hero-title {
    margin: 12px 0 16px;
    font-family: var(--font-script);
    font-size: clamp(2.5rem, 9vw, 8.5rem);
    font-weight: 400;
    line-height: 1.15;
  }

  .hero-caption {
    position: absolute;
    z-index: 2;
    right: 24px;
    bottom: 20px;
    font-size: 0.7rem;
    letter-spacing: 0.12em;
  }

  @media (max-width: 600px) {
    .hero-content {
      padding: 24px 16px 12%;
    }

    .hero-caption {
      display: none;
    }

    .hero-title {
      font-size: clamp(2.5rem, 12vw, 4rem);
    }
  }
</style>
