<script setup lang="ts">
import {ref, onMounted} from 'vue'
import axios from 'axios'
import {apiConfig} from "~/Pages/config";

const productsList = ref([])

const name = ref('')
const numberOfItem = ref('')
const userId = ref('')

async function addProduct() {
  axios.post(`${apiConfig}/product/save`, {
    name: name.value,
    numberOfItem: numberOfItem.value,
    userId: userId.value
  }).then((res) => {
    console.log(res.data)
    callApi();
  })
}

function callApi() {
  axios.get(`${apiConfig}/product/list`).then((res) => {
    //console.log('res',res.data)
    productsList.value = []
    productsList.value.push(...res.data)
    console.log(productsList)
  })
}

onMounted(() => {
  callApi();
})
</script>

<template>
  <div>
    <h1>Lab 4</h1>
  </div>
  <div v-for="product in productsList">
    <h2>{{product.name ?? "no data"}}</h2>
    <p>{{product.id}}</p>
    <p>{{product.numberOfItem}}</p>
    <p>{{product.userId}}</p>
  </div>
  <div>
    <input v-model="name" type="text" placeholder="Name product">
    <input v-model="numberOfItem" type="text" placeholder="Number of item">
    <input v-model="userId" type="text" placeholder="User id">

    <button @click="addProduct">
      add product
    </button>
  </div>

</template>

<style scoped>

</style>