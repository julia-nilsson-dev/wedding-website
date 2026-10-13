<template>
  <footer class="site-footer">
    <p class="footer-message">Vi längtar efter att fira med er</p>

    <div class="footer-divider">
      <span></span>
      <span class="footer-heart">♡</span>
      <span></span>
    </div>

    <p class="footer-date">13 — 15 AUGUSTI · GOTLAND</p>

    <a href="#home" class="back-to-top"> Tillbaka till toppen ↑ </a>

    <p class="footer-copyright">Med kärlek, Alice & Kalle</p>
  </footer>
</template>

<style scoped>
  .site-footer {
    padding: 64px 24px 32px;
    background: #fffdf9;
    color: var(--color-lavender);
    text-align: center;
  }

  .footer-names {
    display: inline-block;
    font-family: var(--font-script);
    font-size: clamp(2.8rem, 6vw, 4rem);
    line-height: 1.1;
    text-decoration: none;
  }

  .footer-names span {
    color: var(--color-sage);
  }

  .footer-message {
    margin: 16px 0 28px;
    color: var(--color-olive);
    font-family: var(--font-heading);
    font-size: 1.4rem;
  }

  .footer-divider {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 14px;
    width: min(100%, 180px);
    margin: 0 auto 24px;
  }

  .footer-divider span:not(.footer-heart) {
    flex: 1;
    height: 1px;
    background: rgb(147 112 158 / 35%);
  }

  .footer-heart {
    font-size: 1.2rem;
  }

  .footer-date {
    margin: 0 0 28px;
    color: var(--color-olive);
    font-size: 0.7rem;
    letter-spacing: 0.17em;
  }

  .back-to-top {
    display: inline-block;
    padding-bottom: 5px;
    border-bottom: 1px solid rgb(147 112 158 / 45%);
    color: var(--color-lavender);
    font-size: 0.75rem;
    letter-spacing: 0.08em;
    text-decoration: none;
  }

  .back-to-top:hover {
    opacity: 0.65;
  }

  .footer-copyright {
    margin: 48px 0 0;
    color: var(--color-olive);
    font-size: 0.72rem;
    opacity: 0.75;
  }

  @media (max-width: 600px) {
    .site-footer {
      padding: 52px 24px 28px;
    }

    .footer-copyright {
      margin-top: 36px;
    }
  }
</style>
