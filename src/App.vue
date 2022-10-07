<script setup lang="ts">
import { ref } from 'vue'
import { getColors } from './utils';
import Color from './components/color.vue';

const color = ref('#1f2937')
const colorResult = ref({})
const messError = ref<string>('')

const find = () => {
  try {
    colorResult.value = getColors(color.value)
    console.log("colorResult", colorResult)
    messError.value = ''
  } catch (e: string) {
    messError.value = e
  }
}
</script>

<template>
  <div>
    <div class="section">
      <input type="text" v-model="color">
      <button @click="find">
      Find Colors
    </button>
    </div>
    <div class="colors">
      <Color v-for="(color, key) in colorResult"  :color="color" :keyc="key" />
    </div>
    <p v-if="messError">
      {{ messError }}
    </p>
  </div>
</template>

<style>
  .section {
    display: flex;
    margin-bottom: 10px;
  }

  p {
    margin: 0;
  }

  button {
    height: 34px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  input {
      margin-right: 10px;
  }

  .colors {
    display: flex;
  }

  .color {
    width: 50px;
    height: 34px;
    margin-right: 10px;
    cursor: pointer;
  }
</style>