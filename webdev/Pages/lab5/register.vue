<script setup lang="ts">
import axios from 'axios'
import {ref} from 'vue'
import {apiConfig} from "~/Pages/config";

const username = ref('')
const password = ref('')
const isError = ref(false)

async function save() {
  const response = await axios.post(`${apiConfig}/auth/register`, {
    userName: username.value,
    passWord: password.value
  })
  if (response.data.dataValue.auth == 1) {
    isError.value = true
  } else {
    //go to login page
    navigateTo('/lab5')
  }
  console.log('isError', isError.value)
  console.log('response', response.data)
}
</script>

<template>
  <div><h1>Register page</h1></div>
  <div v-if="isError">
    <h1>Username or password is exist</h1>
  </div>
  <div>
    <input v-model="username" type="text" class="form-control">
    <input v-model="password" type="text" class="form-control">
  </div>
  <div>
    <button @click="save" class="btn btn-primary">save</button>
  </div>
</template>

<style scoped>

</style>