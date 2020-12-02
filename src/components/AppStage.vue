<template>
  <main>
    <section>
      <chrome-picker v-model="colors1" @input="updateColor1" />
      <section class="selected-color-display" :style="{ backgroundColor: `${selectedColor1.hex}` }" />
    </section>

    <section>
      <sketch-picker v-model="colors2" @input="updateColor2" />
      <section class="selected-color-display" :style="{ backgroundColor: `${selectedColor2.hex}` }" />
    </section>

    <section>
      <ps-picker v-model="colors3" @input="updateColor3" />
      <section class="selected-color-display" :style="{ backgroundColor: `${selectedColor3.hex}` }" />
    </section>
  </main>
</template>

<script>
import { Chrome } from 'vue-color'
import { Sketch } from 'vue-color'
import { Photoshop } from 'vue-color'
import colorList1 from '../fixtures/colors'
import colorList2 from '../fixtures/colors'
import colorList3 from '../fixtures/colors'

const initialColor = {"hsl":{"h":0,"s":0,"l":1,"a":1},"hex":"transparent","hex8":"#FFFFFFFF","rgba":{"r":255,"g":255,"b":255,"a":1},"hsv":{"h":0,"s":0,"v":1,"a":1},"oldHue":0,"source":"hex","a":1}

export default {
  name: 'AppStage',
  components: {
    'chrome-picker': Chrome,
    'sketch-picker': Sketch,
    'ps-picker': Photoshop
  },
  data() {
    return {
      colors1: colorList1,
      selectedColor1: initialColor,
      colors2: colorList2,
      selectedColor2: initialColor,
      colors3: colorList3,
      selectedColor3: initialColor
    }
  },
  methods: {
    updateColor1(value) {
      this.selectedColor1 = value;
    },
    updateColor2(value) {
      this.selectedColor2 = value;
    },
    updateColor3(value) {
      this.selectedColor3 = value;
    }
  }
};
</script>

<style>
section {
  display: flex;
  justify-content: center;
  margin-bottom: 3em;
}

.selected-color-display {
  height: 20em;
  width: 30em;
  border: 5px solid rgba(0,0,0,0.2);
  margin-left: 3em;
}

.vc-chrome {
  max-height: 280px;
}

.vc-sketch {
  max-height: 300px;
}
</style>