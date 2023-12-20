<script setup lang="ts">
import {ref, onMounted} from 'vue'
import axios from 'axios'
import {apiConfig} from "~/Pages/config";

const token = useCookie('token')
const productList = ref([])
console.log('token', token.value)

onMounted(() => {
  axios.get(`${apiConfig}/product-sec/list`, {
    headers: {
      'Authorization': `Bearer ${token.value}`
    }
  }).then((response) => {
    console.log('response', response.data)
    productList.value = response.data.dataValue
  })
})
</script>

<template>
  <div>
    <h1>Home page</h1>
    <a href="/lab5/add">Add</a>
  </div>
  <div v-for="product in productList">
    {{ product.name }} : {{ product.numberOfItem }}
  </div>
</template>

<style scoped>

</style>