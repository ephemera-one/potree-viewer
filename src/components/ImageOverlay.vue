<template>
  <img
    style="z-index: 1; position: absolute; top: 0; left: 0; pointer-events: none;"
    :src="image"
  />
</template>

<script>
export default { props: { image: String } };
</script>

<style scoped>
img {
  z-index: 1;
  position: absolute;
  top: 0;
  left: 0;
  pointer-events: none;
}
</style>
