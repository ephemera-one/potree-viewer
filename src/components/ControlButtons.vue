<template>
  <div>
    <div class="uppercase text-xs">
      {{ title }}
    </div>
    <div class="space-x-5 text-xs">
      <button @click="setButton(0)">LOW</button>
      <button @click="setButton(1)">MID</button>
      <button @click="setButton(2)">HIGH</button>
    </div>
  </div>
</template>
<script>
export default {
  props: { title: String, id: Number },
  data() {
    return {
      buttons: [true, true, true],
    };
  },
  methods: {
    setButton: function(index) {
      const buttons = this.$data.buttons;
      const trueCount = buttons.filter(Boolean).length;

      if (trueCount < 2) return;

      buttons[index] = buttons[index] ? false : true;
    },
    passData: function(data) {
      this.$emit("filterChanged", { id: this.id, data });
    },
  },
};
</script>
