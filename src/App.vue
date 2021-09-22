<template>
  <potree />
  <controls />
</template>

<script setup>
import Potree from "./components/Potree.vue";
import Controls from "./components/Controls.vue";
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
