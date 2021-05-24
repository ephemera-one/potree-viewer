<template>
  <div>
    <potree :pointcloud="pointcloud" />
    <controls :titles="titlesArray" />
  </div>
</template>
<script>
import "@/assets/css/tailwind.css";

import Potree from "./Potree.vue";
import Controls from "./Controls.vue";
export default {
  components: { Potree, Controls },
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
