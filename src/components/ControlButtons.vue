<template>
  <div class="space-y-1">
    <div class="uppercase text-xs underline">
      {{ title }}
    </div>
    <div class="space-x-5">
      <toggle-button :active="buttons[0]" title="LOW" @click="setButton(0)" />
      <toggle-button :active="buttons[1]" title="MID" @click="setButton(1)" />
      <toggle-button :active="buttons[2]" title="HIGH" @click="setButton(2)" />
    </div>
  </div>
</template>
<script>
import ToggleButton from "./ToggleButton.vue";
export default {
  components: { ToggleButton },
  props: { title: String, id: Number },
  data() {
    return {
      buttons: [true, true, true],
    };
  },
  methods: {
    setButton: function(index) {
      console.log(this.buttons);
      const trueCount = this.buttons.filter(Boolean).length;

      if (trueCount < 2 && this.buttons[index]) return;

      this.$set(this.buttons, index, this.buttons[index] ? false : true);

      const selectedButtons = [];
      for (let i = 0; i < 3; i++) {
        if (this.buttons[i]) selectedButtons.push(i);
      }

      this.$emit("filterChanged", { id: this.id, data: selectedButtons });
    },
  },
};
</script>
