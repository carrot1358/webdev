<script lang="ts" setup>
import {ref} from 'vue'

const counter = ref(0)

function compute() {
  counter.value++
}
</script>


<template>
  <div>
    Hello ref {{ counter }}
  </div>
  <div>
    <button @click="compute">Click me</button>
  </div>
  <div>
    <button @click="counter++">Click me</button>
  </div>
</template>

<style scoped>

</style>