<template>
  <button
    class="font-thin"
    :class="[active ? 'text-white' : 'text-gray-400']"
    @click="$emit('click')"
  >
    {{ title }}
  </button>
</template>
<script>
export default {
  props: {
    title: String,
    active: Boolean,
  },
};
</script>
