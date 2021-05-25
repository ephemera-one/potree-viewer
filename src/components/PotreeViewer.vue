<template>
  <div style="height: 100%">
    <potree :pointcloud="pointcloud" />
    <controls :titles="titlesArray" />
  </div>
</template>
<script>
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

<style src="@/assets/css/tailwind.css" />
