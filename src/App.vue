<script setup>
  import SiteNavigation from "./components/SiteNavigation.vue";
  import HeroSection from "./components/HeroSection.vue";
  import AccommodationSection from "./components/AccommodationSection.vue";
  import PracticalInfo from "./components/PracticalInfo.vue";
  import WeekendSchedule from "./components/WeekendSchedule.vue";
  import RsvpSection from "./components/RsvpSection.vue";
  import SpeechSection from "./components/SpeechSection.vue";
  import SiteFooter from "./components/SiteFooter.vue";
  import VideoSection from "./components/VideoSection.vue";
</script>

<template>
  <SiteNavigation />

  <main>
    <HeroSection />
    <VideoSection />
    <WeekendSchedule />
    <PracticalInfo />
    <AccommodationSection />
    <SpeechSection />
    <RsvpSection />
  </main>

  <SiteFooter />
</template>
