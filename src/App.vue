<script setup lang="ts">
import Countdown from './components/Countdown.vue'
</script>

<template>
  <div><img src="./assets/images/the-eras-tour.png" alt="Logo The Eras Tour"></div>
  <Countdown />
</template>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

img {
  width: clamp(200px, 50vw, 500px);
  margin-bottom: 3.5em;
}
</style>
