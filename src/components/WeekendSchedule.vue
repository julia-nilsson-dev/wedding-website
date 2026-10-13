<script setup>
  const days = [
    {
      day: "Fredag",
      date: "13 augusti",
      events: [
        {
          time: "Under dagen",
          title: "Ankomst till Gangvidefarm",
          description: "Checka in, landa och gör er hemmastadda inför helgen.",
        },
        {
          time: "Kväll",
          title: "Middag & mingel",
          description:
            "Vi samlas för en avslappnad kväll med mat, mingel och en första skål tillsammans.",
        },
      ],
    },
    {
      day: "Lördag",
      date: "14 augusti",
      events: [
        {
          time: "14.00",
          title: "Vigsel i När kyrka",
          description:
            "Nu är det äntligen dags! Vi säger ja till varandra i När kyrka.",
        },
        {
          time: "Efter vigseln",
          title: "Bröllopsmiddag på Gangvide Farm",
          description:
            "Vi fortsätter firandet med god mat, tal och skålar tillsammans.",
        },
        {
          time: "Senare på kvällen",
          title: "Fest",
          description: "Vi höjer musiken och firar natten lång tillsammans!",
        },
      ],
    },
    {
      day: "Söndag",
      date: "15 augusti",
      events: [
        {
          time: "Förmiddag",
          title: "Gemensam brunch",
          description:
            "Vi rundar av helgen med en härlig brunch och får tid att umgås en sista gång innan hemfärd.",
        },
      ],
    },
  ];
</script>

<template>
  <section id="weekend" class="weekend-section">
    <div class="weekend-container">
      <div class="section-heading">
        <p class="section-eyebrow">13–15 AUGUSTI</p>
        <h2>Helgens schema</h2>
        <p class="section-intro">
          Tre dagar tillsammans på Gotland, fyllda av kärlek, firande och fina
          stunder.
        </p>
      </div>

      <div class="schedule-grid">
        <article
          v-for="(day, index) in days"
          :key="day.day"
          class="schedule-card"
          :class="{ 'is-wedding-day': day.day === 'Lördag' }"
        >
          <p class="card-date">{{ day.date }}</p>

          <h3>{{ day.day }}</h3>

          <p class="card-subtitle">
            {{
              day.day === "Fredag"
                ? "Välkommen"
                : day.day === "Lördag"
                  ? "Den stora dagen"
                  : "Vi ses igen"
            }}
          </p>

          <div class="card-events">
            <div
              v-for="event in day.events"
              :key="event.title"
              class="card-event"
            >
              <p class="event-time">{{ event.time }}</p>
              <h4>{{ event.title }}</h4>
              <p class="event-description">{{ event.description }}</p>
            </div>
          </div>

          <p class="card-footer">
            {{
              day.day === "Fredag"
                ? "Middag · Mingel"
                : day.day === "Lördag"
                  ? "Vigsel · Middag · Fest"
                  : "Brunch · Avsked"
            }}
          </p>
        </article>
      </div>

      <p class="schedule-note">
        Mer information om tider och helgens upplägg kommer närmare bröllopet.
      </p>
    </div>
  </section>
</template>

<style scoped>
  .weekend-section {
    padding: clamp(80px, 10vw, 140px) 24px;
    background: #fffdf9;
    color: var(--color-olive);
  }

  .weekend-container {
    width: min(100%, 1500px);
    margin: 0 auto;
  }

  .section-heading {
    margin: 0 auto 56px;
    text-align: center;
  }

  .section-eyebrow {
    margin-bottom: 20px;
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
    max-width: 540px;
    margin: 0 auto;
    font-size: 0.95rem;
    line-height: 1.9;
  }

  .schedule-grid {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    border: 1px solid #e5dfd4;
  }

  .schedule-card {
    display: flex;
    flex-direction: column;
    min-width: 0;
    padding: clamp(28px, 3.8vw, 64px);
  }

  .schedule-card + .schedule-card {
    border-left: 1px solid #e5dfd4;
  }

  .schedule-card.is-wedding-day {
    background: #f5eff7;
  }

  .card-date {
    margin: 0 0 16px;
    color: var(--color-lavender);
    font-size: 0.75rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
  }

  .schedule-card h3 {
    margin: 0 0 8px;
    font-family: var(--font-heading);
    font-size: clamp(2rem, 3vw, 3rem);
    font-weight: 400;
  }

  .card-subtitle {
    margin: 0 0 36px;
    color: #a59a6f;
    font-family: var(--font-script);
    font-size: 1.8rem;
  }

  .card-events {
    display: flex;
    flex-direction: column;
    gap: 28px;
    flex: 1;
  }

  .card-event + .card-event {
    padding-top: 24px;
    border-top: 1px solid #e5dfd4;
  }

  .event-time {
    margin: 0 0 8px;
    color: var(--color-lavender);
    font-size: 0.72rem;
    letter-spacing: 0.08em;
  }

  .card-event h4 {
    margin: 0 0 10px;
    font-family: var(--font-heading);
    font-size: 1.45rem;
    font-weight: 500;
  }

  .event-description {
    margin: 0;
    color: #77776f;
    font-size: 0.9rem;
    line-height: 1.9;
  }

  .card-footer {
    margin: 36px 0 0;
    padding-top: 24px;
    border-top: 1px solid #e5dfd4;
    color: var(--color-lavender);
    font-size: 0.72rem;
    letter-spacing: 0.1em;
    line-height: 1.8;
  }

  .schedule-note {
    margin: 28px 0 0;
    color: var(--color-olive);
    font-size: 0.8rem;
    font-style: italic;
    text-align: center;
  }

  @media (max-width: 900px) {
    .schedule-card {
      padding: 28px 22px;
    }

    .card-date {
      letter-spacing: 0.1em;
    }
  }

  @media (max-width: 650px) {
    .section-heading {
      margin-bottom: 40px;
    }

    .schedule-grid {
      grid-template-columns: 1fr;
    }

    .schedule-card + .schedule-card {
      border-left: 0;
      border-top: 1px solid #e5dfd4;
    }

    .schedule-card {
      padding: 32px 26px;
    }

    .schedule-card h3 {
      font-size: 2.5rem;
    }

    .card-subtitle {
      margin-bottom: 28px;
    }
  }
</style>
