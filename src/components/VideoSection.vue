<script setup>
  import { ref } from "vue";
  import heroImage from "../assets/images/hero.jpg";

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

    <div class="video-frame" :class="{ 'is-playing': isPlaying }">
      <!-- YouTube-video -->
      <iframe
        v-if="isPlaying"
        class="save-the-date-video"
        :src="videoUrl"
        title="Alice & Kalles filmhälsning"
        allow="autoplay; encrypted-media; picture-in-picture"
        allowfullscreen
      ></iframe>

      <!-- Omslag med hero-bild -->
      <Transition name="cover">
        <button
          v-if="!isPlaying"
          class="video-cover"
          type="button"
          :style="{ backgroundImage: `url(${heroImage})` }"
          aria-label="Spela upp vår Save the Date-film"
          @click="isPlaying = true"
        >
          <span class="cover-eyebrow"> EN LITEN FILMHÄLSNING </span>

          <span class="cover-title">Alice & Kalle</span>

          <span class="play-button">
            <svg
              viewBox="0 0 24 24"
              width="22"
              height="22"
              fill="currentColor"
              aria-hidden="true"
            >
              <path d="M8 5.5v13l10-6.5z" />
            </svg>
          </span>

          <span class="cover-instruction"> TRYCK FÖR ATT SE FILMEN </span>
        </button>
      </Transition>
    </div>

    <p class="video-caption">GOTLAND · 14 AUGUSTI</p>
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
    opacity: 0;
    transition: opacity 700ms ease;
  }

  .video-frame.is-playing .save-the-date-video {
    opacity: 1;
  }

  /* Omslagsbild */
  .video-cover {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 24px;
    border: 0;
    background-size: cover;
    background-position: center;
    color: #fffdf9;
    cursor: pointer;
  }

  /* Blur och mörk overlay över hela bilden */
  .video-cover::before {
    content: "";
    position: absolute;
    inset: 0;
    background: rgba(40, 40, 35, 0.3);
    backdrop-filter: blur(3px);
    -webkit-backdrop-filter: blur(3px);
  }

  /* Text ovanpå bilden */
  .cover-eyebrow,
  .cover-title,
  .play-button,
  .cover-instruction {
    position: relative;
    z-index: 1;
  }

  .cover-eyebrow {
    margin-bottom: 16px;
    color: #fffdf9;
    font-size: 0.65rem;
    letter-spacing: 0.2em;
  }

  .cover-title {
    font-family: var(--font-script);
    font-size: clamp(2.5rem, 6vw, 4.5rem);
    line-height: 1.15;
  }

  .play-button {
    display: flex;
    width: 58px;
    height: 58px;
    align-items: center;
    justify-content: center;
    margin-top: 28px;
    padding-left: 3px;
    border: 1px solid rgb(255 255 255 / 45%);
    border-radius: 50%;
    background: var(--color-lavender);
    color: #fffdf9;
    transition:
      transform 300ms ease,
      background-color 300ms ease;
  }

  .video-cover:hover .play-button {
    transform: scale(1.08);
    background: #80618b;
  }

  .cover-instruction {
    margin-top: 14px;
    color: #fffdf9;
    font-size: 0.58rem;
    letter-spacing: 0.16em;
  }

  /* Fade-animation */
  .cover-enter-active,
  .cover-leave-active {
    transition:
      opacity 700ms ease,
      transform 700ms ease;
  }

  .cover-leave-to {
    opacity: 0;
    transform: scale(1.02);
  }

  .video-caption {
    margin-top: 24px;
    color: var(--color-olive);
    font-size: 0.7rem;
    letter-spacing: 0.18em;
  }

  /* Mobil */
  @media (max-width: 600px) {
    .save-the-date-header {
      margin-bottom: 32px;
    }

    .video-frame {
      aspect-ratio: 4 / 3;
    }

    .cover-eyebrow {
      font-size: 0.55rem;
      margin-bottom: 10px;
    }

    .cover-title {
      font-size: 2.8rem;
    }

    .play-button {
      width: 50px;
      height: 50px;
      margin-top: 20px;
    }

    .cover-instruction {
      font-size: 0.5rem;
    }
  }

  @media (prefers-reduced-motion: reduce) {
    .save-the-date-video,
    .video-cover,
    .play-button,
    .cover-enter-active,
    .cover-leave-active {
      transition: none;
    }
  }
</style>
