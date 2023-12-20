<script setup lang="ts">
import {ref} from 'vue'
import axios from 'axios'
import {apiConfig} from "~/Pages/config";

const username = ref('')
const password = ref('')
const isError = ref(false)
const token = useCookie('token')

async function submit() {
  const response = await axios.post(`${apiConfig}/auth/login?username=${username.value}&password=${password.value}`)
  console.log('response', response.data)
  const responseData = response.data
  //get error
  if (responseData.dataValue.auth == 1) {
    isError.value = true
  }
  // success
  else {
    token.value = responseData.dataValue.token
    navigateTo('/lab5/home')
  }
}
</script>

<template>
  <div v-if="isError" class="alert alert-danger">
    <h1>Username or password is wrong</h1>
  </div>
  <div>
    <div>
      <input v-model="username" type="text" class="form-control" placeholder="Username">
      <input v-model="password" type="text" class="form-control" placeholder="Password">
    </div>
    <div style="text-align: center">
      <a href="/lab5/register">Register</a>
      <button @click="submit" type="button" class="btn btn-primary">Sign in</button>
    </div>

  </div>
</template>

<style scoped>


</style>