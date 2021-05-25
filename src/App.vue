<template>
  <potree-viewer
    titles="Layer 1, Layer 2, Layer 3"
    pointcloud="pointclouds/final_cloud.laz_converted/metadata.json"
    style="width: 500px; height: 500px"
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
