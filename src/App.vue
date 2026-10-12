<script setup>
import SiteHeader from './components/SiteHeader.vue'
import HeroSection from './components/HeroSection.vue'
import MenuSection from './components/MenuSection.vue'
import StorySection from './components/StorySection.vue'
import VisitSection from './components/VisitSection.vue'
import SiteFooter from './components/SiteFooter.vue'
</script>

<template>
  <SiteHeader />
  <main>
    <HeroSection />
    <MenuSection />
    <StorySection />
    <VisitSection />
  </main>
  <SiteFooter />
</template>
