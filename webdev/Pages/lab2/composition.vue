<script setup lang="ts">
const counter = 0

function compute() {
  console.log("compute")
}
</script>

<template>
  <div>
    {{ counter }}
  </div>
  <div>
    <button @click="compute">Click me !!</button>
  </div>
</template>

<style scoped>

</style>