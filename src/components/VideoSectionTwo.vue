<script setup>
  import { ref } from "vue";

  const isPlaying = ref(false);

  const videoId = "hjxR2CHdp6Q";
  const videoUrl = `https://www.youtube-nocookie.com/embed/${videoId}?autoplay=1&playsinline=1&rel=0&vq=hd1440`;
</script>

<template>
  <section id="welcome" class="save-the-date">
    <div class="save-the-date-header">
      <p class="section-eyebrow">VI VILL BJUDA IN ER</p>

      <h2>
        Till vårt bröllop <br />
        den 14 augusti
      </h2>

      <p class="section-intro">
        En gotländsk bondtjej och en storstadskille – ibland blir livet lite
        bättre än man kunnat tänka sig. Nu väntar ett nytt kapitel, och vi ser
        fram emot att få fira det tillsammans med er på Gotland.
      </p>
    </div>

    <div class="video-frame">
      <iframe
        class="save-the-date-video"
        :src="videoUrl"
        title="Alice & Kalles filmhälsning"
        allow="encrypted-media; picture-in-picture"
        allowfullscreen
        referrerpolicy="strict-origin-when-cross-origin"
      ></iframe>
    </div>
  </section>
</template>

<style scoped>
  .save-the-date {
    padding: clamp(72px, 10vw, 140px) 24px;
    background: var(--color-cream);
    color: var(--color-olive);
    text-align: center;
  }

  .save-the-date-header {
    max-width: 680px;
    margin: 0 auto 48px;
  }

  .section-eyebrow {
    margin-bottom: 20px;
    color: var(--color-lavender);
    font-size: 0.72rem;
    letter-spacing: 0.22em;
  }

  .save-the-date h2 {
    max-width: 620px;
    margin: 0 auto 20px;
    font-family: var(--font-heading);
    font-size: clamp(2.5rem, 5vw, 4.5rem);
    font-weight: 400;
    line-height: 1.1;
  }

  .section-intro {
    max-width: 460px;
    margin: 0 auto;
    font-size: 0.95rem;
    line-height: 1.9;
  }

  /* Videoram */
  .video-frame {
    position: relative;
    width: min(100%, 900px);
    aspect-ratio: 16 / 9;
    margin: 0 auto;
    overflow: hidden;
    background: #e9e6dc;
    border: 1px solid rgb(86 87 77 / 12%);
  }

  /* YouTube-video */
  .save-the-date-video {
    display: block;
    width: 100%;
    height: 100%;
    border: 0;
  }

  /* Mobil */
  @media (max-width: 600px) {
    .save-the-date-header {
      margin-bottom: 32px;
    }

    .video-frame {
      aspect-ratio: 4 / 3;
    }
  }
</style>
