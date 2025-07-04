<script setup>
// import HeroSection from "./components/HeroSection.vue";
import FeaturesSection from "./components/FeaturesSection.vue";
import CtaSection from "./components/CtaSection.vue";
import ContactSection from "./components/ContactSection.vue";
import PricingSection from "./components/PricingSection.vue";
import FooterSection from "./components/FooterSection.vue";
import AppNavbar from "./components/AppNavbar.vue";
</script>

<template>
  <div class="relative min-h-screen w-full" style="touch-action: manipulation;">
    <AppNavbar />
    <!-- <HeroSection /> -->
    <FeaturesSection />
    <CtaSection />
    <ContactSection />
    <PricingSection />
    <FooterSection />
  </div>
</template>

<style scoped></style>
