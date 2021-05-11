<template>
  <v-card id="controls" flat class="py-12">
    <v-card-text>
      <v-row align="center" justify="center">
        <v-col cols="12">
          <p class="text-center">
            Multiple
          </p>
        </v-col>
        <v-btn-toggle v-model="toggle_exclusive" mandatory multiple>
          <v-btn>
            Low
          </v-btn>
          <v-btn>
            Mid
          </v-btn>
          <v-btn>
            High
          </v-btn>
        </v-btn-toggle>

        <v-col cols="12" class="text-center">
          Model: {{ toggle_exclusive }}
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>
<script>
export default {
  data() {
    return {
      toggle_exclusive: [0, 1, 2],
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
