<template>
  <potree-viewer
    titles="Layer 1, Layer 2, Layer 3"
    pointcloud="pointclouds/final_cloud.laz_converted/metadata.json"
  />
</template>

<script>
import "@/assets/css/tailwind.css";

import PotreeViewer from "./components/PotreeViewer.vue";

export default {
  name: "App",
  components: {
    PotreeViewer,
  },
};
</script>
