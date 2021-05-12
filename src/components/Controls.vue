<template>
  <v-card id="controls" flat class="py-5">
    <control-buttons :id="0" @filterChanged="filterData" :title="titles[0]" />
    <control-buttons :id="1" @filterChanged="filterData" :title="titles[1]" />
    <control-buttons :id="2" @filterChanged="filterData" :title="titles[2]" />
  </v-card>
</template>
<script>
import ControlButtons from "./ControlButtons.vue";
import { VCard } from "vuetify/lib";

function combos(list, n = 0, result = [], current = []) {
  if (n === list.length) result.push(current);
  else
    list[n].forEach((item) => combos(list, n + 1, result, [...current, item]));

  return result;
}

function calculateIndex(selectedOptions) {
  let indexValue = 0;

  for (let i = 0; i < 3; i++) {
    let value = selectedOptions[i];

    indexValue += value * Math.pow(3, 2 - i);
  }

  return indexValue;
}

function disableAll() {
  for (let i = 0; i < 27; i++) {
    window.viewer.setClassificationVisibility(i, false);
  }
}

function enableClass(index) {
  window.viewer.setClassificationVisibility(index, true);
}

export default {
  components: { ControlButtons, VCard },
  props: {
    titles: Array,
  },
  methods: {
    filterData: function(data) {
      this.filters[data.id] = data.data.sort();

      let filtersArray = [];
      for (let i = 0; i < 3; i++) {
        filtersArray.push(this.filters[i]);
      }

      const combinations = combos(filtersArray);

      disableAll();

      combinations.forEach((c) => {
        let index = calculateIndex(c);

        enableClass(index);
      });
    },
  },
  data() {
    return {
      filters: {
        0: [0, 1, 2],
        1: [0, 1, 2],
        2: [0, 1, 2],
      },
    };
  },
};
</script>
<style scoped>
#controls {
  position: absolute;
  z-index: 15;
  top: 0;
  left: 0;
}
</style>
