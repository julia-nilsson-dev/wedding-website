<script setup>
  import { ref } from "vue";

  const information = [
    {
      number: "01",
      title: "Ett barnfritt firande",
      text: [
        "Den här helgen låter vi barnen få en egen semester medan vi firar tillsammans. Bröllopet och boendet är därför barnfritt. Vi älskar era barn men den här helgen älskar vi eran barnvakt.",
      ],
    },
    {
      number: "02",
      title: "Klädkod – Kostym",
      text: "För herrar rekommenderas kostym med skjorta, samt slips eller fluga. För damer rekommenderas klänning, kjol, byxdress av festligare karaktär med längd nedanför knäna. Vi välkomnar somriga pastellfärger och toner.",
    },
    {
      number: "03",
      title: "Bröllopsgåva",
      text: "Er närvaro på vår bröllopsdag är den finaste gåvan vi kan önska oss. För den som ändå önskar uppmärksamma oss med en bröllopsgåva tar vi tacksamt emot ett bidrag till vår kommande bröllopsresa.",
    },
    {
      number: "04",
      title: "Hitta hit",
      text: [
        {
          before: "Vigseln äger rum i ",
          linkText: "När kyrka",
          after: ", 623 48 När.",
          url: "https://www.google.com/maps/place//data=!4m2!3m1!1s0x46f76ea866b1c45d:0xb33afbf6a129315e",
        },
        {
          before: "Bröllopsmiddagen tillbringas på ",
          linkText: "Gangvide",
          after: ", När Gangvide 503, 623 48 Stånga.",
          url: "https://www.google.com/maps/place//data=!4m2!3m1!1s0x46f76bfc6b1f66e5:0x302956f41f55d0e4",
        },
        {
          text: "Vi erbjuder transport till och från kyrkan med utgångspunkt från Gangvide.",
        },
      ],
    },
    {
      number: "05",
      title: "Mer information kommer",
      text: "Vi uppdaterar sidan löpande med mer information inför bröllopet. Titta gärna in här igen när det närmar sig!",
    },
  ];

  const openItem = ref(null);

  function toggleItem(index) {
    openItem.value = openItem.value === index ? null : index;
  }
</script>

<template>
  <section id="practical-info" class="practical-section">
    <div class="practical-container">
      <p class="section-eyebrow">BRA ATT VETA</p>

      <h2>Praktisk information</h2>

      <p class="section-intro">
        Här har vi samlat sådant som kan vara bra att veta inför vårt bröllop.
      </p>

      <div class="info-list">
        <article
          v-for="(item, index) in information"
          :key="item.number"
          class="info-item"
          :class="{ 'is-open': openItem === index }"
        >
          <button
            class="info-toggle"
            type="button"
            :aria-expanded="openItem === index"
            @click="toggleItem(index)"
          >
            <span class="info-number">{{ item.number }}</span>
            <span class="info-title">{{ item.title }}</span>
            <span class="info-icon" aria-hidden="true">
              {{ openItem === index ? "−" : "+" }}
            </span>
          </button>

          <div
            class="info-answer-clip"
            :class="{ 'is-open': openItem === index }"
            :aria-hidden="openItem !== index"
          >
            <div class="info-answer-inner">
              <div class="info-answer">
                <p
                  v-for="(paragraph, paragraphIndex) in Array.isArray(item.text)
                    ? item.text
                    : [item.text]"
                  :key="paragraphIndex"
                >
                  <template v-if="typeof paragraph === 'string'">
                    {{ paragraph }}
                  </template>

                  <template v-else>
                    <template v-if="paragraph.text">
                      {{ paragraph.text }}
                    </template>
                    <template v-else>
                      {{ paragraph.before
                      }}<a
                        :href="paragraph.url"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="info-link"
                        >{{ paragraph.linkText }}</a
                      >{{ paragraph.after }}
                    </template>
                  </template>
                </p>
              </div>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .practical-section {
    padding: clamp(80px, 12vw, 150px) 24px;
    background: var(--color-cream);
    color: var(--color-lavender);
  }

  .practical-container {
    width: min(100%, 850px);
    margin: 0 auto;
  }

  .section-eyebrow {
    margin-bottom: 24px;
    color: rgb(147 112 158 / 75%);
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    text-align: center;
  }

  .practical-section h2 {
    margin: 0 0 24px;
    font-family: var(--font-heading);
    font-size: clamp(2.8rem, 6vw, 5rem);
    font-weight: 400;
    line-height: 1.1;
    text-align: center;
  }

  .section-intro {
    max-width: 540px;
    margin: 0 auto 64px;
    font-size: 0.95rem;
    line-height: 1.9;
    text-align: center;
  }

  .info-list {
    border-top: 1px solid rgb(147 112 158 / 25%);
  }

  .info-item {
    border-bottom: 1px solid rgb(147 112 158 / 25%);
  }

  .info-toggle {
    display: grid;
    grid-template-columns: 54px 1fr 24px;
    align-items: center;
    gap: 16px;
    width: 100%;
    padding: 26px 0;
    border: 0;
    background: transparent;
    color: inherit;
    text-align: left;
    cursor: pointer;
  }

  .info-number {
    font-family: var(--font-heading);
    font-size: 1.35rem;
  }

  .info-title {
    font-family: var(--font-heading);
    font-size: clamp(1.45rem, 3vw, 2rem);
  }

  .info-icon {
    display: inline-block;
    font-size: 1.4rem;
    text-align: center;
    transition: transform 0.35s ease;
  }

  .info-item.is-open .info-icon {
    transform: rotate(180deg);
  }

  /* Animerar höjden mjukt utan att behöva gissa en max-height. */
  .info-answer-clip {
    display: grid;
    grid-template-rows: 0fr;
    transition: grid-template-rows 0.5s cubic-bezier(0.22, 1, 0.36, 1);
  }

  .info-answer-clip.is-open {
    grid-template-rows: 1fr;
  }

  .info-answer-inner {
    min-height: 0;
    overflow: hidden;
  }

  .info-answer {
    padding: 0 40px 28px 70px;
    opacity: 0;
    transform: translateY(-8px);
    transition:
      opacity 0.35s ease,
      transform 0.5s cubic-bezier(0.22, 1, 0.36, 1);
  }

  .info-answer-clip.is-open .info-answer {
    opacity: 1;
    transform: translateY(0);
    transition-delay: 0.05s;
  }

  .info-answer p {
    max-width: 600px;
    margin: 0;
    font-size: 0.95rem;
    line-height: 1.9;
  }

  .info-answer p + p {
    margin-top: 1.2em;
  }
  .info-toggle:focus-visible {
    outline: 1px solid var(--color-lavender);
    outline-offset: 5px;
  }

  .info-link {
    color: var(--color-lavender);
    text-decoration: underline;
    text-decoration-color: rgb(147 112 158 / 45%);
    text-underline-offset: 4px;
    transition:
      color 0.2s ease,
      text-decoration-color 0.2s ease;
  }

  .info-link:hover {
    color: var(--color-olive);
    text-decoration-color: var(--color-olive);
  }

  .info-link:focus-visible {
    outline: 1px solid var(--color-lavender);
    outline-offset: 3px;
  }

  @media (max-width: 600px) {
    .section-intro {
      margin-bottom: 42px;
    }

    .info-toggle {
      grid-template-columns: 32px 1fr 20px;
      gap: 12px;
      padding: 22px 0;
    }

    .info-answer {
      padding: 0 20px 24px 44px;
    }
  }

  @media (prefers-reduced-motion: reduce) {
    .info-icon,
    .info-answer-clip,
    .info-answer {
      transition: none;
    }
  }
</style>
