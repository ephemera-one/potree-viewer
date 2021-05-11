<template>
  <v-app>
    <v-main>
      <potree />
      <controls />
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

  data: () => ({
    //
  }),
};
</script>
