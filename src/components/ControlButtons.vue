<template>
  <div>
    <div class="uppercase text-xs underline">
      {{ title }}
    </div>
    <div class="space-x-5 text-xs">
      <button
        class="font-thin"
        :class="[buttons[0] ? 'text-white' : 'text-gray-400']"
        @click="setButton(0)"
      >
        LOW
      </button>
      <button
        class="font-thin"
        :class="[buttons[1] ? 'text-white' : 'text-gray-400']"
        @click="setButton(1)"
      >
        MID
      </button>
      <button
        class="font-thin"
        :class="[buttons[2] ? 'text-white' : 'text-gray-400']"
        @click="setButton(2)"
      >
        HIGH
      </button>
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
