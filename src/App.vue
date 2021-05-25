<template>
  <potree-viewer
    titles="Layer 1, Layer 2, Layer 3"
    image1="/assets/test.png"
    image2="/assets/test.png"
    image1title="More Info"
    image2title="Super Info"
    pointcloud="pointclouds/final_cloud.laz_converted/metadata.json"
    style="width: 100%; height: 100%"
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
