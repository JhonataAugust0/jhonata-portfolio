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
}

.experience-content {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  align-content: flex-end;
  align-self: flex-end;
  justify-content: flex-end;
  justify-items: flex-end;

  //position: absolute;
}
</style>