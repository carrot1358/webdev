<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  data() {
    return {
      counter: 0
    }
  },
  methods: {
    compute() {
      console.log("compute")
    }

  }
})
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