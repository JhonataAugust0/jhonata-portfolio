<script setup lang="ts">
import PresentationHeader from '@/components/PresentationHeader.vue'
import AboutMe from '@/components/AboutMe.vue'
import SkillsSection from '@/components/SkillsSection.vue'

</script>

<template>
  <main>
    <div class="home">
      <PresentationHeader />
      <AboutMe />
      <SkillsSection />
    </div>
  </main>
</template>

<style>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>