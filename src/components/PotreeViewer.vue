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
<style>
html * {
  font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif,
    "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
}
</style>
