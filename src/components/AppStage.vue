<template>
  <main>
    <h1>App Stage</h1>

    <chrome-picker v-model="colors" @input="updateColor" />

    <section class="selected-color-display" :style="{ backgroundColor: `${selectedColor.hex}` }" />
  </main>
</template>

<script>
import { Chrome } from 'vue-color'
import colorList from '../fixtures/colors'

export default {
  name: 'AppStage',
  components: {
    'chrome-picker': Chrome
  },
  data() {
    return {
      colors: colorList,
      selectedColor: null
    }
  },
  methods: {
    updateColor(value) {
      this.selectedColor = value;
    }
  }
};
</script>

<style>
.selected-color-display {
  height: 20em;
  width: 30em;
}
</style>