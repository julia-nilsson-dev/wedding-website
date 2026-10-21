<script setup>
  import { ref, onMounted, onUnmounted } from "vue";

  const menuOpen = ref(false);
  const isScrolled = ref(false);

  const links = [
    { label: "Praktisk information", href: "#practical-info" },
    { label: "Resa & Boende", href: "#accommodation" },
    { label: "Helgen", href: "#weekend" },
    { label: "Anmälan tal", href: "#speeches" },
  ];

  function handleScroll() {
    isScrolled.value = window.scrollY > 50;
  }

  onMounted(() => {
    handleScroll();
    window.addEventListener("scroll", handleScroll, { passive: true });
  });

  onUnmounted(() => {
    window.removeEventListener("scroll", handleScroll);
  });
</script>

<template>
  <header
    class="site-header"
    :class="{
      'is-scrolled': isScrolled,
      'menu-is-open': menuOpen,
    }"
  >
    <a
      class="site-logo"
      :class="{ 'logo-visible': isScrolled || menuOpen }"
      href="#home"
      @click="menuOpen = false"
    >
      Alice & Kalle
    </a>

    <button
      class="menu-toggle"
      type="button"
      :aria-expanded="menuOpen"
      :aria-label="menuOpen ? 'Stäng meny' : 'Öppna meny'"
      @click="menuOpen = !menuOpen"
    >
      <span :class="{ 'is-open': menuOpen }" class="menu-icon">
        <span></span>
        <span></span>
        <span></span>
      </span>
    </button>

    <nav class="site-nav" :class="{ 'is-open': menuOpen }">
      <a
        v-for="link in links"
        :key="link.href"
        :href="link.href"
        @click="menuOpen = false"
      >
        {{ link.label }}
      </a>

      <a class="nav-rsvp" href="#rsvp" @click="menuOpen = false"> OSA </a>
    </nav>
  </header>
</template>

<style scoped>
  .site-header {
    position: fixed;
    z-index: 100;
    top: 0;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding: 22px 3%;
    color: var(--color-lavender);
    background-color: transparent;
    transition:
      background-color 0.4s ease,
      box-shadow 0.4s ease,
      backdrop-filter 0.4s ease;
  }

  .site-header.is-scrolled {
    background-color: rgb(248 244 239 / 88%);
    box-shadow: 0 4px 20px rgb(86 87 77 / 6%);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
  }

  .site-header.menu-is-open {
    background-color: var(--color-cream);
    backdrop-filter: none;
    -webkit-backdrop-filter: none;
    box-shadow: none;
  }

  .site-logo {
    font-family: var(--font-script);
    font-size: 1.8rem;
    text-decoration: none;
    white-space: nowrap;

    opacity: 0;
    visibility: hidden;
    transform: translateY(-6px);

    transition:
      opacity 0.5s ease,
      transform 0.5s ease,
      visibility 0.5s ease;
  }

  .site-logo.logo-visible {
    opacity: 1;
    visibility: visible;
    transform: translateY(0);
  }

  .site-nav {
    display: flex;
    align-items: center;
    gap: clamp(16px, 2.5vw, 42px);
  }

  .site-nav a {
    color: inherit;
    font-size: 0.75rem;
    letter-spacing: 0.16em;
    text-decoration: none;
    text-transform: uppercase;
    padding: 4px 0 2px 0;
    border-bottom: 1px solid transparent;
  }

  .site-nav a:hover {
    opacity: 1;
    border-bottom: 1px solid var(--color-lavender);
  }

  .site-nav .nav-rsvp {
    border-radius: 8px;
    background-color: var(--color-lavender);
    border: 1px solid var(--color-lavender);
    color: var(--color-cream);
    padding: 8px 25px;
  }

  .site-nav .nav-rsvp:hover {
    color: var(--color-lavender);
    background-color: transparent;
    border-radius: 8px;
    opacity: 1;
  }

  .menu-toggle {
    display: none;
    align-items: center;
    justify-content: center;
    width: 46px;
    height: 46px;
    padding: 8px;
    border: 1px solid var(--color-cream);
    border-radius: 50%;
    /* border: none; */
    background: transparent;
    color: var(--color-olive);
    cursor: pointer;
    transition:
      background-color 0.3s ease,
      border-color 0.3s ease;
  }

  .menu-toggle:hover {
    background-color: rgb(86 87 77 / 8%);
    border-color: var(--color-olive);
  }

  .menu-icon {
    position: relative;
    display: block;
    width: 25px;
    height: 18px;
  }

  .menu-icon span {
    position: absolute;
    left: 0;
    width: 25px;
    height: 1.5px;
    background-color: var(--color-cream);
    border-radius: 2px;
    transform-origin: center;
    transition:
      top 0.3s ease,
      transform 0.3s ease,
      opacity 0.2s ease;
  }

  .menu-icon span:first-child {
    top: 2px;
  }

  .menu-icon span:nth-child(2) {
    top: 8px;
  }

  .menu-icon span:last-child {
    top: 14px;
  }

  /* Förvandla strecken till ett symmetriskt X */
  .menu-icon.is-open span:first-child {
    top: 8px;
    transform: rotate(45deg);
  }

  .menu-icon.is-open span:nth-child(2) {
    opacity: 0;
  }

  .menu-icon.is-open span:last-child {
    top: 8px;
    transform: rotate(-45deg);
  }

  @media (max-width: 900px) {
    .site-header {
      padding: 12px 12px;
      color: var(--color-lavender);
    }
    .site-logo {
      padding-top: 7px;
    }
    .menu-toggle {
      display: flex;
    }

    .site-nav {
      position: absolute;
      top: 100%;
      left: 0;
      display: flex;
      flex-direction: column;
      align-items: stretch;
      gap: 0;
      width: 100%;
      min-height: calc(100vh - 70px);
      min-height: calc(100svh - 70px);
      padding: 12px 6% 24px;
      background: var(--color-cream);

      opacity: 0;
      visibility: hidden;
      pointer-events: none;
      transform: translateY(-12px);

      transition:
        opacity 0.35s ease,
        transform 0.4s ease,
        visibility 0.4s ease;
    }

    .site-nav.is-open {
      opacity: 1;
      visibility: visible;
      pointer-events: auto;
      transform: translateY(0);
    }

    .site-nav a {
      padding: 16px 0;
    }

    .site-nav .nav-rsvp {
      text-align: center;
      margin-top: 8px;
    }
  }
</style>
