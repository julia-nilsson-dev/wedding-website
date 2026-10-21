<script setup>
  import saveTheDateVideo from "../assets/videos/save-the-date.mov";
</script>

<template>
  <section id="welcome" class="save-the-date">
    <div class="save-the-date-header">
      <p class="section-eyebrow">VI VILL BJUDA IN ER</p>
      <h2>Vi längtar efter att fira med er</h2>
      <p class="section-intro">
        En gotländsk bondtjej och en storstadskille – ibland blir livet lite
        bättre än man kunnat tänka sig. Nu väntar ett nytt kapitel, och vi
        längtar efter att få fira det tillsammans med er på Gotland!
      </p>
    </div>

    <div class="video-frame">
      <video
        class="save-the-date-video"
        controls
        playsinline
        preload="metadata"
      >
        <source :src="saveTheDateVideo" type="video/mp4" />
        Your browser does not support this video.
      </video>
    </div>

    <p class="video-caption">GOTLAND · 13–15 AUGUST</p>
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

  .video-frame {
    width: min(100%, 1000px);
    margin: 0 auto;
    overflow: hidden;
    background: #e8e3db;
  }

  .save-the-date-video {
    display: block;
    width: 100%;
    height: auto;
    max-height: 80svh;
    object-fit: contain;
  }

  .video-caption {
    margin-top: 24px;
    font-size: 0.7rem;
    letter-spacing: 0.18em;
  }

  @media (max-width: 600px) {
    .save-the-date-header {
      margin-bottom: 32px;
    }

    .video-frame {
      width: 100%;
    }
  }
</style>
