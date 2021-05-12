<template>
  <v-app>
    <link
      rel="stylesheet"
      href="https://fonts.googleapis.com/css?family=Roboto:100,300,400,500,700,900"
    />
    <link
      rel="stylesheet"
      href="https://cdn.jsdelivr.net/npm/@mdi/font@latest/css/materialdesignicons.min.css"
    />
    <link
      href="https://cdn.jsdelivr.net/npm/vuetify/dist/vuetify.min.css"
      rel="stylesheet"
    />
    <v-main>
      <potree :pointcloud="pointcloud" />
      <controls :titles="titlesArray" />
    </v-main>
  </v-app>
</template>
<script>
import Potree from "./Potree.vue";
import Controls from "./Controls";
import vuetify from "../plugins/vuetify";
import { VApp, VMain } from "vuetify/lib";
export default {
  vuetify,
  components: { Potree, Controls, "v-app": VApp, "v-main": VMain },
  props: {
    titles: String,
    pointcloud: String,
  },
  computed: {
    titlesArray() {
      return this.titles.split(",");
    },
  },
};
</script>
