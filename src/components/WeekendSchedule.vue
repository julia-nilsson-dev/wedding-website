<script setup>
  const events = [
    {
      time: "13.15",
      title: "Avfärd till kyrkan",
      description:
        "För er som bor på Gangvide åker vi gemensamt mot När kyrka.",
      note: "För boende på Gangvide",
      type: "transport",
    },
    {
      time: "13.30",
      title: "Gästerna på plats",
      description:
        "Vi ber alla gäster att vara på plats i kyrkan i god tid före vigseln.",
      type: "arrival",
    },
    {
      time: "14.00",
      title: "Vigsel i När kyrka",
      description:
        "Nu är det äntligen dags! Vi samlas för att fira kärleken och att säga ja till varandra.",
      type: "ceremony",
    },
    {
      title: "Mingel på Gangvide",
      description:
        "Vi åker gemensamt till gården för mingel. Njut av bubbel och snittar medan vi skålar för brudparet.",
      type: "mingling",
    },
    {
      title: "Bröllopsmiddag",
      description:
        "Toasmasters hälsar alla välkomna och presenterar kvällens program.",
      type: "dinner",
    },
    {
      title: "Brudvisning",
      description:
        "Vi samlas för brudvisning och njuter av gotlandsdricke och kringlor innan festen drar igång.",
      type: "tradition",
    },
    {
      title: "Fest!",
      description:
        "Nu höjer vi musiken, fyller dansgolvet och firar tillsammans långt in på natten.",
      type: "party",
    },
  ];
</script>

<template>
  <section id="weekend" class="weekend-section">
    <div class="weekend-container">
      <header class="section-heading">
        <p class="section-eyebrow">LÖRDAG 14 AUGUSTI</p>

        <h2>Den stora dagen</h2>

        <p class="section-intro">
          En dag fylld av kärlek, gotländska traditioner, god mat och fest.
        </p>
      </header>

      <div class="schedule">
        <div class="timeline">
          <article
            v-for="(event, index) in events"
            :key="event.title"
            class="timeline-event"
            :class="`event-${event.type}`"
          >
            <div class="timeline-marker" aria-hidden="true">
              <svg
                class="timeline-heart"
                viewBox="0 0 24 24"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M12 21 C10.5 19.5 2 12.5 2 7.5 C2 3.5 7 1.5 12 6.5 C17 1.5 22 3.5 22 7.5 C22 12.5 13.5 19.5 12 21 Z"
                  fill="currentColor"
                />
              </svg>
            </div>

            <div class="timeline-content">
              <p v-if="event.time" class="event-time">{{ event.time }}</p>

              <h3>{{ event.title }}</h3>

              <p class="event-description">
                {{ event.description }}
              </p>

              <p v-if="event.note" class="event-note">
                {{ event.note }}
              </p>
            </div>
          </article>
          <div class="timeline-marker" aria-hidden="true">
            <svg
              class="timeline-heart"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M12 21 C10.5 19.5 2 12.5 2 7.5 C2 3.5 7 1.5 12 6.5 C17 1.5 22 3.5 22 7.5 C22 12.5 13.5 19.5 12 21 Z"
                fill="currentColor"
              />
            </svg>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .weekend-section {
    padding: clamp(80px, 10vw, 140px) 24px;
    background: #f5eff7;
    color: var(--color-lavender);
  }

  .weekend-container {
    width: min(100%, 1000px);
    margin: 0 auto;
  }

  .section-heading {
    max-width: 650px;
    margin: 0 auto 80px;
    text-align: center;
  }

  .section-eyebrow {
    margin: 0 0 20px;
    color: var(--color-lavender);
    font-size: 0.72rem;
    letter-spacing: 0.22em;
  }

  .weekend-section h2 {
    margin: 0 0 20px;
    font-family: var(--font-heading);
    font-size: clamp(2.8rem, 6vw, 5rem);
    font-weight: 400;
    line-height: 1.1;
  }

  .section-intro {
    max-width: 520px;
    margin: 0 auto;
    font-size: 0.95rem;
    line-height: 1.9;
  }

  .schedule {
    display: flex;
    flex-direction: column;
    align-items: center;
    grid-template-columns: 190px minmax(0, 1fr);
    gap: clamp(30px, 6vw, 80px);
  }

  .schedule-date {
    position: sticky;
    top: 110px;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 35px 20px;
    background: #f5eff7;
    border: 1px solid #e5dfd4;
    text-align: center;
  }

  .date-day {
    font-family: var(--font-heading);
    font-size: 5.5rem;
    font-weight: 400;
    line-height: 1;
  }

  .date-month {
    margin-top: 10px;
    color: var(--color-lavender);
    font-size: 0.85rem;
    letter-spacing: 0.16em;
    text-transform: uppercase;
  }

  .date-weekday {
    margin-top: 14px;
    font-family: var(--font-script);
    font-size: 2rem;
  }

  .timeline {
    position: relative;
  }

  .timeline::before {
    position: absolute;
    top: 12px;
    bottom: 12px;
    left: 19px;
    width: 1px;
    background: #ded3e2;
    content: "";
    z-index: 0;
    pointer-events: none;
  }

  .timeline-event {
    position: relative;
    display: grid;
    grid-template-columns: 40px minmax(0, 1fr);
    gap: 24px;
    padding-bottom: 38px;
  }

  .timeline-event:last-child {
    padding-bottom: 0;
  }

  .timeline-marker {
    position: relative;
    z-index: 2;
    display: flex;
    width: 40px;
    height: 40px;
    flex-shrink: 0;
    align-items: center;
    justify-content: center;

    border: none;
    background: #f5eff7;
    color: var(--color-lavender);

    font-size: 1.25rem;
    line-height: 1;
  }

  .timeline-content {
    padding: 3px 0 30px;
    border-bottom: 1px solid #e5dfd4;
  }

  .timeline-event:last-child .timeline-content {
    border-bottom: 0;
  }

  .event-time {
    margin: 0 0 9px;
    color: var(--color-lavender);
    font-size: 0.72rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }

  .timeline-content h3 {
    margin: 0 0 10px;
    font-family: var(--font-heading);
    font-size: clamp(1.5rem, 2.5vw, 2rem);
    font-weight: 400;
    line-height: 1.25;
  }

  .event-description {
    max-width: 540px;
    margin: 0;
    color: #77776f;
    font-size: 0.9rem;
    line-height: 1.9;
  }

  .event-note {
    display: inline-block;
    margin: 14px 0 0;
    padding: 7px 12px;
    background: var(--color-blush);
    color: var(--color-lavender);
    font-size: 0.72rem;
    letter-spacing: 0.04em;
  }

  .schedule-note {
    margin: 55px 0 0;
    color: #77776f;
    font-size: 0.8rem;
    font-style: italic;
    line-height: 1.8;
    text-align: center;
  }

  .timeline-heart {
    display: block;
    width: 24px;
    height: 24px;
    color: var(--color-lavender);
    overflow: visible;
  }

  @media (max-width: 650px) {
    .section-heading {
      margin-bottom: 48px;
    }

    .schedule {
      grid-template-columns: 1fr;
      gap: 38px;
    }

    .schedule-date {
      position: static;
      width: 100%;
      padding: 22px;
    }

    .date-day {
      font-size: 4rem;
    }

    .date-month {
      margin-top: 6px;
    }

    .date-weekday {
      margin-top: 5px;
    }

    .timeline-event {
      grid-template-columns: 34px minmax(0, 1fr);
      gap: 16px;
      padding-bottom: 28px;
    }

    .timeline::before {
      left: 16px;
    }

    .timeline-marker {
      width: 34px;
      height: 34px;
      font-size: 1.1rem;
    }

    .timeline-content {
      padding-top: 2px;
      padding-bottom: 25px;
    }

    .timeline-content h3 {
      font-size: 1.6rem;
    }

    .schedule-note {
      margin-top: 35px;
    }
  }
</style>
