<script setup>
  import { ref } from "vue";

  const showForm = ref(false);

  const attending = ref("");

  const name = ref("");

  const phone = ref("");

  const wantsAccommodation = ref("");

  const foodPreferences = ref("");

  const songRequest = ref("");

  const funFact = ref("");

  const showNotice = ref(false);

  const isSubmitting = ref(false);

  async function submitRsvp() {
    if (isSubmitting.value) return;

    isSubmitting.value = true;
    showNotice.value = false;

    const data = {
      name: name.value,
      phone: phone.value,
      attending: attending.value,
      wantsAccommodation: wantsAccommodation.value,
      foodPreferences: foodPreferences.value,
      songRequest: songRequest.value,
      funFact: funFact.value,
    };

    try {
      await fetch(
        "https://script.google.com/macros/s/AKfycbxudoB7DD2zogWEu_uG4r-iipjTxE08XTYf3VinB2YRaxPu_c8r_m9pFdy9YotFQFcG2Q/exec",
        {
          method: "POST",
          mode: "no-cors",
          headers: {
            "Content-Type": "text/plain;charset=utf-8",
          },
          body: JSON.stringify(data),
        },
      );

      showNotice.value = true;
    } catch (error) {
      console.error("Kunde inte skicka anmälan:", error);
      alert("Det gick inte att skicka ditt svar. Försök gärna igen.");
    } finally {
      isSubmitting.value = false;
    }
  }
</script>

<template>
  <section id="rsvp" class="rsvp-section">
    <div class="rsvp-container">
      <div class="rsvp-heading">
        <p class="section-eyebrow">VI HOPPAS ATT DU KOMMER</p>

        <h2>Vill du fira med oss?</h2>

        <p class="rsvp-deadline">Svara senast 14 februari</p>

        <p class="rsvp-intro">
          Nu närmar sig vår stora dag och vi hoppas att du vill vara med och
          fira den tillsammans med oss! Fyll i formuläret nedan och meddela om
          du kommer, så att vi kan börja planera för en oförglömlig helg
          tillsammans.
        </p>
      </div>

      <div class="rsvp-form-wrapper">
        <Transition name="fade">
          <button
            v-if="!showForm && !showNotice"
            class="rsvp-submit"
            type="button"
            @click="showForm = true"
          >
            Svara på inbjudan
          </button>
        </Transition>

        <Transition name="form-reveal">
          <form
            v-if="showForm && !showNotice"
            class="rsvp-form"
            @submit.prevent="submitRsvp"
          >
            <div class="form-section">
              <p class="form-section-label">01 — OM DIG</p>

              <div class="field">
                <label for="guest-name">För- och efternamn *</label>

                <input
                  id="guest-name"
                  v-model="name"
                  type="text"
                  autocomplete="name"
                  placeholder="Ditt fullständiga namn"
                  required
                />
              </div>

              <div class="field">
                <label for="guest-phone">Telefonnummer</label>

                <input
                  id="guest-phone"
                  v-model="phone"
                  type="tel"
                  name="phone"
                  autocomplete="tel"
                  placeholder="Ditt telefonnummer"
                />

                <p class="field-hint">
                  Så att våra toastmasters kan kontakta dig vid behov.
                </p>
              </div>
            </div>

            <div class="form-section">
              <p class="form-section-label">02 — DIN NÄRVARO</p>

              <fieldset class="choice-field">
                <legend>Kommer du på bröllopet? *</legend>

                <label class="choice-option">
                  <input
                    v-model="attending"
                    type="radio"
                    name="attending"
                    value="yes"
                    required
                    @change="wantsAccommodation = ''"
                  />

                  <span>Ja, jag kommer gärna!</span>
                </label>

                <label class="choice-option">
                  <input
                    v-model="attending"
                    type="radio"
                    name="attending"
                    value="no"
                    required
                    @change="wantsAccommodation = ''"
                  />

                  <span>Nej, tyvärr kan jag inte komma</span>
                </label>
              </fieldset>

              <div v-if="attending === 'yes'" class="conditional-fields">
                <fieldset class="choice-field">
                  <legend>
                    Önskar du kostnadsfritt boende på Gangvidefarm den 13–15
                    augusti? *
                  </legend>

                  <p class="field-hint">
                    Boendet erbjuds till gäster som reser till Gotland från
                    fastlandet.
                  </p>

                  <label class="choice-option">
                    <input
                      v-model="wantsAccommodation"
                      type="radio"
                      name="accommodation"
                      value="yes"
                      required
                    />

                    <span>Ja, jag önskar boende</span>
                  </label>

                  <label class="choice-option">
                    <input
                      v-model="wantsAccommodation"
                      type="radio"
                      name="accommodation"
                      value="no"
                      required
                    />

                    <span>Nej tack, jag ordnar boende själv</span>
                  </label>
                </fieldset>

                <div class="field">
                  <label for="food-preferences">
                    Allergier & matpreferenser
                  </label>

                  <textarea
                    id="food-preferences"
                    v-model="foodPreferences"
                    rows="3"
                    placeholder="Berätta gärna om allergier eller specialkost"
                  ></textarea>
                </div>
              </div>
            </div>

            <div v-if="attending === 'yes'" class="form-section bonus-section">
              <p class="form-section-label">03 — LÄR KÄNNA DIG LITE BÄTTRE</p>

              <p class="bonus-intro">
                Nu till det lite roligare! Hjälp oss att göra festen ännu mer
                personlig.
              </p>

              <div class="field">
                <label for="song-request">
                  Vilken låt får inte saknas på dansgolvet?
                </label>

                <input
                  id="song-request"
                  v-model="songRequest"
                  type="text"
                  placeholder="Artist och låt"
                />
              </div>

              <div class="field">
                <label for="fun-fact">
                  Vad är något som få andra gäster vet om dig?
                </label>

                <textarea
                  id="fun-fact"
                  v-model="funFact"
                  rows="3"
                  placeholder="Avslöja något oväntat..."
                ></textarea>
              </div>
            </div>

            <div class="form-footer">
              <p class="required-note">* Obligatoriska fält</p>

              <button
                class="rsvp-submit"
                type="submit"
                :disabled="isSubmitting"
                :aria-busy="isSubmitting"
              >
                <span
                  v-if="isSubmitting"
                  class="loader"
                  aria-hidden="true"
                ></span>
                <span>
                  {{
                    isSubmitting ? "Skickar ditt svar..." : "Skicka mitt svar"
                  }}
                </span>
              </button>
            </div>
          </form>
        </Transition>

        <Transition name="form-reveal">
          <div
            v-if="showNotice"
            class="rsvp-thank-you"
            role="status"
            aria-live="polite"
          >
            <p class="section-eyebrow">TACK FÖR DITT SVAR</p>
            <h3>Tack för att du svarade!</h3>
            <p>Vi ser fram emot att fira tillsammans med dig på Gotland.♡</p>
          </div>
        </Transition>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .rsvp-section {
    padding: clamp(80px, 10vw, 150px) 24px;

    background: #f5eff7;

    color: var(--color-lavender);
  }

  .rsvp-container {
    width: min(100%, 760px);

    margin: 0 auto;
  }

  .rsvp-heading {
    max-width: 600px;

    margin: 0 auto 56px;

    text-align: center;
  }

  .section-eyebrow {
    margin-bottom: 20px;

    color: var(--color-olive);

    font-size: 0.72rem;

    letter-spacing: 0.2em;
  }

  .rsvp-heading h2 {
    margin: 0 0 12px;

    font-family: var(--font-heading);

    font-size: clamp(4rem, 9vw, 7rem);

    font-weight: 400;

    line-height: 1;
  }

  .rsvp-deadline {
    margin: 20px 0;

    color: var(--color-olive);

    font-size: 0.78rem;

    letter-spacing: 0.12em;

    text-transform: uppercase;
  }

  .rsvp-intro {
    max-width: 600px;

    margin: 0 auto;

    font-size: 0.95rem;

    line-height: 1.9;
  }

  .rsvp-form {
    padding: clamp(24px, 5vw, 56px);

    background: #fffdf9;

    border: 1px solid rgb(147 112 158 / 18%);
  }

  .form-section + .form-section {
    margin-top: 48px;

    padding-top: 40px;

    border-top: 1px solid rgb(147 112 158 / 25%);
  }

  .form-section-label {
    margin: 0 0 28px;

    color: var(--color-olive);

    font-size: 0.7rem;

    letter-spacing: 0.17em;
  }

  .field {
    display: flex;

    flex-direction: column;

    gap: 10px;

    margin-bottom: 26px;
  }

  .field:last-child {
    margin-bottom: 0;
  }

  .field label,
  .choice-field legend {
    color: var(--color-olive);

    font-size: 0.9rem;

    font-weight: 500;
  }

  .field input,
  .field textarea {
    width: 100%;

    padding: 15px 16px;

    border: 1px solid #ded5e1;

    border-radius: 0;

    outline: none;

    background: #fffdf9;

    color: var(--color-olive);

    font-size: 0.9rem;

    line-height: 1.6;

    transition: border-color 0.2s;
  }
  .field input:focus,
  .field textarea:focus {
    border-color: var(--color-lavender);
  }

  .field input::placeholder,
  .field textarea::placeholder {
    color: #a6a19f;
  }

  .field textarea {
    resize: vertical;
  }

  .choice-field {
    min-width: 0;

    margin: 0 0 30px;

    padding: 0;

    border: 0;
  }

  .choice-field legend {
    margin-bottom: 18px;

    line-height: 1.7;
  }

  .field-hint {
    margin: -8px 0 16px;

    color: #77776f;

    font-size: 0.82rem;

    line-height: 1.7;
  }

  .choice-option {
    display: flex;

    align-items: flex-start;

    gap: 12px;

    margin: 14px 0;

    color: var(--color-olive);

    font-size: 0.9rem;

    line-height: 1.6;

    cursor: pointer;
  }

  .choice-option input {
    width: 17px;

    height: 17px;

    margin: 2px 0 0;

    flex: 0 0 auto;

    accent-color: var(--color-lavender);
  }

  .conditional-fields {
    margin-top: 32px;

    padding-top: 30px;

    border-top: 1px solid rgb(147 112 158 / 18%);
  }

  .bonus-intro {
    margin: -12px 0 28px;

    color: #77776f;

    font-size: 0.9rem;

    line-height: 1.8;
  }

  .form-footer {
    margin-top: 42px;

    padding-top: 28px;

    border-top: 1px solid rgb(147 112 158 / 25%);

    text-align: center;
  }

  .required-note {
    margin: 0 0 24px;

    color: #77776f;

    font-size: 0.75rem;

    text-align: left;
  }

  .rsvp-submit {
    display: inline-flex;

    align-items: center;

    justify-content: center;

    gap: 24px;

    min-width: 220px;

    padding: 17px 26px;

    border: 1px solid var(--color-lavender);

    background: var(--color-lavender);

    color: #fffdf9;

    font-size: 0.75rem;

    letter-spacing: 0.1em;

    text-transform: uppercase;

    cursor: pointer;

    transition:
      background 0.2s,
      color 0.2s;
  }

  .rsvp-submit:hover {
    background: transparent;

    color: var(--color-lavender);
  }

  .rsvp-submit:disabled {
    opacity: 0.8;
    cursor: wait;
  }

  .loader {
    width: 16px;
    height: 16px;
    flex-shrink: 0;
    border: 2px solid rgb(255 253 249 / 40%);
    border-top-color: #fffdf9;
    border-radius: 50%;
    animation: rsvp-spin 0.8s linear infinite;
  }

  @keyframes rsvp-spin {
    to {
      transform: rotate(360deg);
    }
  }

  @media (prefers-reduced-motion: reduce) {
    .loader {
      animation-duration: 1.8s;
    }
  }

  .form-notice {
    margin: 24px 0 0;

    color: var(--color-olive);

    font-size: 0.85rem;

    line-height: 1.8;
  }

  @media (max-width: 600px) {
    .rsvp-heading {
      margin-bottom: 36px;
    }

    .rsvp-form {
      padding: 26px 20px;
    }

    .form-section + .form-section {
      margin-top: 36px;

      padding-top: 32px;
    }

    .rsvp-submit {
      width: 100%;
    }
  }

  .rsvp-form-wrapper {
    display: flex;

    flex-direction: column;

    align-items: center;
  }

  .rsvp-form {
    width: 100%;

    margin-top: 32px;
  }

  .rsvp-form-wrapper > .rsvp-submit {
    margin: 0 auto;
  }

  .fade-enter-active,
  .fade-leave-active {
    transition:
      opacity 0.3s ease,
      transform 0.3s ease;
  }

  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;

    transform: translateY(8px);
  }

  .form-reveal-enter-active,
  .form-reveal-leave-active {
    transition:
      opacity 0.65s ease,
      transform 0.65s cubic-bezier(0.22, 1, 0.36, 1);
  }

  .form-reveal-enter-from,
  .form-reveal-leave-to {
    opacity: 0;

    transform: translateY(20px);
  }

  @media (prefers-reduced-motion: reduce) {
    .fade-enter-active,
    .fade-leave-active,
    .form-reveal-enter-active,
    .form-reveal-leave-active {
      transition: none;
    }
  }

  .rsvp-thank-you {
    width: 100%;
    margin-top: 32px;
    padding: 48px 24px;
    background: #fffdf9;
    border: 1px solid rgb(147 112 158 / 18%);
    text-align: center;
  }

  .rsvp-thank-you h3 {
    margin: 16px 0;
    font-family: var(--font-heading);
    font-size: clamp(2.5rem, 6vw, 4rem);
    font-weight: 400;
    line-height: 1.1;
  }

  .rsvp-thank-you > p:last-child {
    max-width: 420px;
    margin: 0 auto;
    font-size: 0.95rem;
    line-height: 1.9;
  }
</style>
