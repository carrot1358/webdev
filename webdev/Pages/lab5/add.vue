<script setup lang="ts">
import {ref} from 'vue'
import axios from 'axios'
import {apiConfig} from "~/Pages/config";

const token = useCookie('token')
const name = ref('')
const numberOfItem = ref(0)

async function additem() {
  const response = await axios.post(`${apiConfig}/product-sec/save`, {
    name: name.value,
    numberOfItem: numberOfItem.value
  }, {
    headers: {
      'Authorization': `Bearer ${token.value}`
    }
  })
  navigateTo('/lab5/home')
}

</script>

<template>
  <div>
    <input v-model="name" type="text" class="form-control">
    <input v-model="numberOfItem" type="text" class="form-control">
    <button @click="additem" class="btn btn-primary">Add</button>
  </div>
</template>

<style scoped>

</style>