<script setup lang="ts">
import PresentationHeader from '@/components/PresentationHeader.vue'
import AboutMe from '@/components/AboutMe.vue'

</script>

<template>
  <main>
    <div class="home">
      <div class="container-1">
        <PresentationHeader />
      </div>

      <div class="container-2">
        <AboutMe />
      </div>
    </div>
  </main>
</template>

<style scoped>
.home {
  display: grid;
  flex-wrap: wrap;
  flex-direction: column;
  flex-flow: column;
}

.container-1 {
  order: 1;
}

.container-2 {
  order: 2;
}
</style>