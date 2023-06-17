<script setup>
import Clock from './components/Clock.vue'
</script>

<template>
  <Clock label="US East coast" flag="us" timezone="America/New_York" />
  <Clock label="Belgium" flag="be" timezone="Europe/Brussels" />
  <Clock label="Australia" flag="au" timezone="Australia/Sydney" />
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Poiret+One');
@import url('https://fonts.googleapis.com/css2?family=Roboto+Mono&display=swap');
@import url('https://cdn.jsdelivr.net/gh/lipis/flag-icons@6.6.6/css/flag-icons.min.css');
</style>
