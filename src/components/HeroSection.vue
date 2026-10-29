<script setup>
  import heroImage from "../assets/images/hero.jpg";
  import heroImageMobile from "../assets/images/hero_mobile.png";
</script>

<template>
  <section id="home" class="hero">
    <div class="hero-image-container">
      <picture>
        <source media="(max-width: 900px)" :srcset="heroImageMobile" />

        <img
          class="hero-image"
          :src="heroImage"
          alt="Alice och Kalle på Gotland"
        />
      </picture>
    </div>

    <div class="hero-overlay"></div>

    <div class="hero-content">
      <p class="hero-eyebrow">GOTLAND</p>
      <h1 class="hero-title">Alice & Kalle</h1>
      <p class="hero-date">14 AUGUSTI</p>
    </div>
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

  @supports (height: 98svh) {
    .hero-image-container {
      height: auto;
    }

    .hero-image {
      width: 100%;
      height: 100vh;
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
    font-size: clamp(2.5rem, 9vw, 8.5rem);
    font-weight: 400;
    line-height: 1.15;
    font-family: var(--font-script);
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
    .hero {
      place-items: start center;
    }

    .hero-content {
      align-self: start;
      padding: 90px 16px 24px;
    }

    .hero-caption {
      display: none;
    }

    .hero-title {
      font-size: clamp(3.5rem, 15vw, 5.5rem);
      margin: 16px 0 12px;
      line-height: 1.1;
    }

    .hero-eyebrow,
    .hero-date {
      font-size: clamp(0.9rem, 3.5vw, 1.2rem);
      letter-spacing: 0.22em;
      line-height: 1.8;
    }

    .hero-overlay {
      background: linear-gradient(
        to bottom,
        rgba(40, 42, 35, 0.35) 0%,
        rgba(40, 42, 35, 0.05) 60%,
        rgba(40, 42, 35, 0.1) 100%
      );
    }
  }
</style>
