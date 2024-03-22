<script setup lang="ts">
import PresentationHeader from '@/components/PresentationHeader.vue'
import AboutMe from '@/components/AboutMe.vue'

</script>

<template>
  <main>
    <div class="home">
      <PresentationHeader />
      <AboutMe />
    </div>
  </main>
</template>

<style scoped>
.home {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  flex-flow: column;
}
</style>