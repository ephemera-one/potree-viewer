<template>
  <div style="height: 100%">
    <potree :pointcloud="pointcloud" />
    <controls
      @imageChanged="enableImage"
      :titles="titlesArray"
      :imageTitles="imageTitles"
    />
    <image-overlay :image="image1" v-if="images[0]" />
    <image-overlay :image="image2" v-if="images[1]" />
  </div>
</template>
<script>
import Potree from "./Potree.vue";
import Controls from "./Controls.vue";
import ImageOverlay from "./ImageOverlay.vue";

export default {
  components: { Potree, Controls, ImageOverlay },
  data() {
    return { images: [true, true] };
  },
  props: {
    titles: String,
    pointcloud: String,
    image1: String,
    image2: String,
    image1title: String,
    image2title: String,
  },
  computed: {
    titlesArray() {
      return this.titles.split(",");
    },
    imageTitles() {
      return [this.image1title, this.image2title];
    },
  },
  methods: {
    enableImage: function(data) {
      let { id, enabled } = data;

      this.$set(this.images, id, enabled);
    },
  },
};
</script>

<style src="@/assets/css/tailwind.css" />
