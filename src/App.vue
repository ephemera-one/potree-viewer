<template>
  <v-app>
    <v-main>
      <potree />
      <controls :titles="titles" />
    </v-main>
  </v-app>
</template>

<script>
import Controls from "./components/Controls.vue";
import Potree from "./components/Potree.vue";

export default {
  name: "App",

  components: {
    Potree,
    Controls,
  },

  data() {
    return {
      titles: ["Layer 1", "Layer 2", "Layer 3"],
    };
  },
};
</script>
