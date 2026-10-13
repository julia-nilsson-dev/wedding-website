<script setup>
  import { ref, onMounted, onUnmounted } from "vue";

  const menuOpen = ref(false);
  const isScrolled = ref(false);

  const links = [
    { label: "Helgen", href: "#weekend" },
    { label: "Resa & Boende", href: "#accommodation" },
    { label: "Praktisk information", href: "#practical-info" },
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
      aria-label="Öppna meny"
      @click="menuOpen = !menuOpen"
    >
      {{ menuOpen ? "Close" : "Menu" }}
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
    color: var(--color-olive);
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
    padding: 8px 10px;
  }

  .site-nav a:hover {
    opacity: 1;
    background-color: rgb(86 87 77 / 25%);
    border-radius: 10px;
  }

  .site-nav .nav-rsvp {
    border-radius: 8px;
    background-color: var(--color-lavender);
    color: var(--color-cream);
    padding: 8px 25px;
  }

  .site-nav .nav-rsvp:hover {
    color: var(--color-lavender);
    background-color: var(--color-blush);
    border-color: var(--color-blush);
    border-radius: 8px;
    opacity: 1;
  }

  .menu-toggle {
    display: none;
    color: inherit;
    background: transparent;
    border: 1px solid currentColor;
    padding: 10px 14px;
    font: inherit;
  }

  @media (max-width: 900px) {
    .site-header {
      padding: 20px 6%;
    }

    .menu-toggle {
      display: block;
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
