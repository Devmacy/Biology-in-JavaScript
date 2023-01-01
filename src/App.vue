<script setup>
import HardyWeinberg from "./components/HardyWeinberg.vue";
import CoinFlip from "./components/CoinFlip.vue";
</script>

<template>
  <HardyWeinberg></HardyWeinberg>
  <div style="border-top:10px solid #59207a;margin: 5px 0"></div>

  <coin-flip></coin-flip>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
