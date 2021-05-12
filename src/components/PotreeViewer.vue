<template>
  <v-app>
    <v-main>
      <potree />
      <controls :titles="titles" />
    </v-main>
  </v-app>
</template>
<script>
import Potree from "./Potree.vue";
import Controls from "./Controls";
export default {
  components: { Potree, Controls },
  data() {
    return {
      titles: ["Layer 1", "Layer 2", "Layer 3"],
    };
  },
};
</script>
