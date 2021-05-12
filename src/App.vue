<template>
  <potree-viewer
    titles="Layer 1, Layer 2, Layer 3"
    pointcloud="pointclouds/final_cloud.laz_converted/metadata.json"
  />
</template>

<script>
import PotreeViewer from "./components/PotreeViewer.vue";

export default {
  name: "App",
  components: {
    PotreeViewer,
  },
};
</script>
