<script setup lang="ts">
import PresentationHeader from '@/components/PresentationHeader.vue'
import AboutMe from '@/components/AboutMe.vue'
import SkillsSection from '@/components/SkillsSection.vue'
import ExperiencesSection from '@/components/ExperiencesSection.vue'

</script>

<template>
  <main>
    <div class="home">
      <PresentationHeader />
      <AboutMe />
      <SkillsSection />
      <ExperiencesSection />
    </div>

  </main>
</template>

<style>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 2rem;
  left: 0;
  top: 0;
  margin: 0 auto;
}
</style>