<script setup>
import Clock from './components/Clock.vue'
</script>

<template>
  <main>
    <ul>
      <li>
        <Clock />
      </li>
      <li>
        <Clock />
      </li>
      <li>
        <Clock />
      </li>
    </ul>
  </main>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Poiret+One');

ul {
  display: flex;
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  flex: 1;
}
</style>
