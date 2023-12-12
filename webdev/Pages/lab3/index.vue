<script setup lang="ts">
import {ref , onMounted} from 'vue'

const lstData = ref([{product: "test", price: "20"}, {product: "test2", price: "99"}])
const username = ref("")
function onClick() {
  lstData.value.push({product: "ccc", price: "201"})
}
function printuser(){
  console.log(username.value)
}

onMounted(() => {
  console.log("starting page")
})
</script>

<template>
  <div v-for="data in lstData">
    {{ data.product }} : {{ data.price }}
  </div>
  <div>
    <button @click="onClick">Add ccc</button>
  </div>
  <div>
    <input type="text" v-model="username">
  </div>
  <div>
    <button @click="printuser">Print Username</button>
  </div>

</template>

<style scoped>

</style>