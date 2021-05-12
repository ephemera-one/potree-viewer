<template>
  <v-row align="center" justify="center">
    <v-col cols="12" class="text-center">
      {{ title }}
    </v-col>
    <v-btn-toggle
      v-model="selectedButtons"
      @change="passData"
      mandatory
      multiple
    >
      <v-btn small>
        Low
      </v-btn>
      <v-btn small>
        Mid
      </v-btn>
      <v-btn small>
        High
      </v-btn>
    </v-btn-toggle>
  </v-row>
</template>
<script>
export default {
  props: { title: String, id: Number },
  data() {
    return {
      selectedButtons: [0, 1, 2],
    };
  },
  methods: {
    passData: function(data) {
      this.$emit("filterChanged", { id: this.id, data });
    },
  },
};
</script>
