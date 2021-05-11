<template>
  <div id="app">
    <potree />
    <controls />
  </div>
</template>

<script>
import Potree from "./components/Potree.vue";
import Controls from "./components/Controls.vue";

export default {
  name: "App",
  components: {
    Potree,
    Controls,
  },
};
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
