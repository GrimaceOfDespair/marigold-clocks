<script setup>
import Clock from './components/Clock.vue'
</script>

<template>
  <Clock label="US West coast" flag="us" timezone="America/Los_Angeles" />
  <Clock label="US East coast" flag="us" timezone="America/New_York" />
  <Clock label="Europe" flag="eu" timezone="Europe/Brussels" />
  <Clock label="India" flag="in" timezone="Asia/Kolkata" />
  <Clock label="Australia" flag="au" timezone="Australia/Sydney" />
  <Clock label="New Zealand" flag="nz" timezone="Pacific/Auckland" />
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Poiret+One');
@import url('https://fonts.googleapis.com/css2?family=Roboto+Mono&display=swap');
@import url('https://cdn.jsdelivr.net/gh/lipis/flag-icons@6.6.6/css/flag-icons.min.css');
</style>
