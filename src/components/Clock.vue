<template>
  <div class="container">
    <div class="clock">
      <div>
        <div class="info date">{{ time }}<br />{{ day }}<br />{{ date }}</div>
        <div class="info label">{{ label }}</div>
        <div class="flag"><span class="fi fib" :class="'fi-' + flag"></span></div>
      </div>
      <div class="dot"></div>
      <div>
        <div class="hand hour-hand" :style="{ transform: 'rotate(' + hDeg + 'deg)'}"></div>
        <div class="hand minute-hand" :style="{ transform: 'rotate(' + mDeg + 'deg)'}"></div>
        <div class="hand second-hand" :style="{ transform: 'rotate(' + sDeg + 'deg)'}"></div>
      </div>
      <div>
        <span class="h3">3</span>
        <span class="h6">6</span>
        <span class="h9">9</span>
        <span class="h12">12</span>
      </div>
      <div class="diallines" v-for="n in 60" :style="{ transform: 'rotate(' + 6 * (n - 1) + 'deg)' }"></div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  label: String,
  flag: String,
  timezone: String,
})

const weekday = [
  "Sunday",
  "Monday",
  "Tuesday",
  "Wednesday",
  "Thursday",
  "Friday",
  "Saturday"
];

const hDeg = ref(0);
const mDeg = ref(0);
const sDeg = ref(0);
const day = ref(weekday[0]);
const date = ref('');
const time = ref('');

function clock() {
  const
    localDate = new Date(),
    timezoneDate = new Date(localDate.toLocaleString('en-US', { timeZone: props.timezone })),
    hours = timezoneDate.getHours(),
    minutes = timezoneDate.getMinutes(),
    seconds = timezoneDate.getSeconds();
        
  hDeg.value = hours * 30 + minutes * (360/720),
  mDeg.value = minutes * 6 + seconds * (360/3600),
  sDeg.value = seconds * 6;
  date.value = timezoneDate.toLocaleDateString("en-US", {
    year: "numeric",
    month: "short",
    day: "numeric"
  });
  time.value = timezoneDate.toLocaleTimeString("en-US");
  day.value = weekday[timezoneDate.getDay()];
}

setInterval(() => clock(), 100);

</script>

<style scoped>

.container {
  zoom: .75;
}

.clock {
  background: #ececec;
  width: 300px;
  height: 300px;
  margin: 8% auto 0;
  border-radius: 50%;
  border: 14px solid #333;
  position: relative;
  box-shadow: 0 2vw 4vw -1vw rgba(0,0,0,0.8);
}

.dot {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: #ccc;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  margin: auto;
  position: absolute;
  z-index: 10;
  box-shadow: 0 2px 4px -1px black;
}

.hand {
  position: absolute;
  left: 50%;
  border-top-left-radius: 50%;
  border-top-right-radius: 50%;
}

.hour-hand {
  z-index: 5;
  width: 4px;
  height: 65px;
  background: #333;
  top: 79px;
  margin-left: -2px;
  transform-origin: 50% 72px;
}

.minute-hand {
  z-index: 6;
  width: 4px;
  height: 100px;
  background: #666;
  top: 46px;
  margin-left: -2px;
  transform-origin: 50% 105px;
}

.second-hand {
  z-index: 7;
  width: 2px;
  height: 120px;
  background: gold;
  top: 26px;
  margin-left: -1px;
  transform-origin: 50% 125px;
}

span {
  display: inline-block;
  position: absolute;
  color: #333;
  font-size: 22px;
  font-family: 'Poiret One';
  font-weight: 700;
  z-index: 4;
}

.h12 {
  top: 30px;
  left: 50%;
  margin-left: -9px;
}
.h3 {
  top: 140px;
  right: 30px;
}
.h6 {
  bottom: 30px;
  left: 50%;
  margin-left: -5px;
}
.h9 {
  left: 32px;
  top: 140px;
}

.diallines {
  position: absolute;
  z-index: 2;
  width: 2px;
  height: 15px;
  background: #666;
  left: 50%;
  margin-left: -2px;
  transform-origin: 50% 150px;
}

.diallines:nth-of-type(5n) {
  width: 4px;
  height: 25px;
}

.flag {
  position: absolute;
  top: 180px;
  height: 20px;
  width: 30px;
  margin-left: -15px;
  z-index: 3;
  left: 50%;
}

.info {
  position: absolute;
  border-radius: 7px;
  background: #ddd;
  border: 1px solid #ccc;
  border-bottom-color: #eee;
  border-right-color: #eee;
  text-align: center;
  line-height: 20px;
  color: #444;
  font-size: 11px;
  margin-left: -60px;
  font-family: 'Roboto Mono', monospace;
  z-index: 3;
  letter-spacing: 3px;
  left: 50%;
}

.date {
  margin-left: -70px;
  top: 70px;
  width: 140px;
  height: 60px;
}

.label {
  margin-left: -70px;
  top: 210px;
  width: 140px;
  height: 20px;
}

</style>