<template>
  <section id="accommodation" class="accommodation-section">
    <div class="accommodation-content">
      <p class="section-eyebrow">BOENDE PÅ GOTLAND</p>

      <h2>Långvägars?</h2>

      <p class="accommodation-intro">
        Reser du långt för att fira med oss? Vi erbjuder kostnadsfritt boende på
        Gangvide under bröllopshelgen. För dig som bor på gården väntar dessutom
        lite extra tid tillsammans, från fredag till söndag. Ange gärna i din
        anmälan om du önskar boende.
      </p>

      <div class="accommodation-details">
        <div class="detail-item">
          <span class="detail-number" aria-hidden="true">
            <svg
              class="detail-heart"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M12 21 C10.5 19.5 2 12.5 2 7.5 C2 3.5 7 1.5 12 6.5 C17 1.5 22 3.5 22 7.5 C22 12.5 13.5 19.5 12 21 Z"
                fill="currentColor"
              />
            </svg>
          </span>
          <div>
            <p class="detail-eyebrow">13 AUGUSTI</p>
            <h3>Fredag – välkommen till gården</h3>
            <p>
              Under dagen checkar ni in, landar och gör er hemmastadda på
              Gangvide. På kvällen samlas vi för en avslappnad middag och lite
              mingel – en mysig start på bröllopshelgen.
            </p>
            <span class="detail-note">För boende på Gangvide</span>
          </div>
        </div>

        <div class="detail-item">
          <span class="detail-number" aria-hidden="true">
            <svg
              class="detail-heart"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M12 21 C10.5 19.5 2 12.5 2 7.5 C2 3.5 7 1.5 12 6.5 C17 1.5 22 3.5 22 7.5 C22 12.5 13.5 19.5 12 21 Z"
                fill="currentColor"
              />
            </svg>
          </span>
          <div>
            <p class="detail-eyebrow">14 AUGUSTI</p>
            <h3>Lördag – den stora dagen</h3>
            <p>
              Nu är det dags att fira kärleken! Vi åker gemensamt till När kyrka
              för vigsel.
            </p>
          </div>
        </div>

        <div class="detail-item">
          <span class="detail-number" aria-hidden="true">
            <svg
              class="detail-heart"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M12 21 C10.5 19.5 2 12.5 2 7.5 C2 3.5 7 1.5 12 6.5 C17 1.5 22 3.5 22 7.5 C22 12.5 13.5 19.5 12 21 Z"
                fill="currentColor"
              />
            </svg>
          </span>
          <div>
            <p class="detail-eyebrow">15 AUGUSTI</p>
            <h3>Söndag – en lugn avslutning</h3>
            <p>
              Vi rundar av helgen tillsammans med en härlig brunch, tid att
              umgås och möjlighet att säga hej då innan det är dags att bege sig
              hemåt.
            </p>
            <span class="detail-note">För boende på Gangvide</span>
          </div>
        </div>

        <div class="detail-item">
          <span class="detail-number" aria-hidden="true">
            <svg
              class="detail-heart"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M12 21 C10.5 19.5 2 12.5 2 7.5 C2 3.5 7 1.5 12 6.5 C17 1.5 22 3.5 22 7.5 C22 12.5 13.5 19.5 12 21 Z"
                fill="currentColor"
              />
            </svg>
          </span>
          <div>
            <p class="detail-eyebrow">BRA ATT VETA</p>
            <h3>Resan till Gotland</h3>
            <p>
              Augusti är en populär månad att besöka Gotland, så vi
              rekommenderar att ni bokar färja eller flyg i god tid. Det går
              inte att resa kollektivt hela vägen till Gangvide. Om du inte har
              tillgång till bil, hör gärna av dig i god tid så försöker vi
              hjälpa till med transporten.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .accommodation-section {
    padding: clamp(80px, 12vw, 160px) 24px;
    /* background: #f5eff7; */
    background-color: #e9e9e3;
    color: var(--color-olive);
  }

  .accommodation-content {
    width: min(100%, 900px);
    margin: 0 auto;
  }

  .section-eyebrow {
    margin: 0 0 24px;
    color: var(--color-olive);
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    text-align: center;
  }

  .accommodation-section h2 {
    margin: 0 0 24px;
    font-family: var(--font-heading);
    font-size: clamp(3rem, 7vw, 5.5rem);
    font-weight: 400;
    line-height: 1.05;
    text-align: center;
  }

  .accommodation-intro {
    max-width: 580px;
    margin: 0 auto 72px;
    font-size: 1rem;
    line-height: 1.9;
    text-align: center;
  }

  .accommodation-details {
    border-top: 1px solid rgb(86 87 77 / 25%);
  }

  .detail-item {
    display: grid;
    grid-template-columns: 70px minmax(0, 1fr);
    gap: 24px;
    padding: 32px 0;
    border-bottom: 1px solid rgb(86 87 77 / 25%);
  }

  .detail-number {
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding-top: 5px;
    color: var(--color-olive);
  }

  .detail-heart {
    display: block;
    width: 24px;
    height: 24px;
    color: var(--color-olive);
    overflow: visible;
  }

  .detail-eyebrow {
    margin: 0 0 10px;
    color: var(--color-lavender);
    font-size: 0.7rem;
    letter-spacing: 0.16em;
  }

  .detail-item h3 {
    margin: 0 0 10px;
    font-family: var(--font-heading);
    font-size: 1.8rem;
    font-weight: 500;
  }

  .detail-item p:not(.detail-eyebrow) {
    max-width: 620px;
    margin: 0;
    font-size: 0.95rem;
    line-height: 1.8;
  }

  .detail-note {
    display: inline-block;
    margin-top: 14px;
    padding: 7px 12px;
    background: rgb(255 253 249 / 70%);
    color: var(--color-lavender);
    font-size: 0.72rem;
    letter-spacing: 0.04em;
  }

  .accommodation-link {
    display: inline-flex;
    align-items: center;
    gap: 14px;
    margin-top: 20px;
    padding-bottom: 8px;
    border-bottom: 1px solid var(--color-olive);
    color: inherit;
    font-size: 0.78rem;
    letter-spacing: 0.08em;
    text-decoration: none;
    text-transform: uppercase;
  }

  .accommodation-link:hover {
    opacity: 0.65;
  }

  @media (max-width: 600px) {
    .accommodation-intro {
      margin-bottom: 48px;
    }

    .detail-item {
      grid-template-columns: 36px minmax(0, 1fr);
      gap: 14px;
      padding: 26px 0;
    }

    .detail-item h3 {
      font-size: 1.55rem;
    }
  }
</style>
