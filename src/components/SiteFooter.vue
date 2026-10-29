<template>
  <footer class="site-footer">
    <p class="footer-message">
      Vi längtar efter att få samla våra favoritmänniskor på vår favoritö.
    </p>

    <div class="footer-divider">
      <span></span>
      <svg
        class="footer-heart"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
        aria-hidden="true"
      >
        <path
          d="M12 21 C10.5 19.5 2 12.5 2 7.5 C2 3.5 7 1.5 12 6.5 C17 1.5 22 3.5 22 7.5 C22 12.5 13.5 19.5 12 21 Z"
          fill="none"
          stroke="currentColor"
          stroke-width="1.4"
          stroke-linejoin="round"
        />
      </svg>
      <span></span>
    </div>

    <p class="footer-date">14 AUGUSTI · GOTLAND</p>

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
    display: block;
    flex-shrink: 0;
    width: 22px;
    height: 22px;
    color: var(--color-lavender);
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
