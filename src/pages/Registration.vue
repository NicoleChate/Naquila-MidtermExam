<template>
  <div>
    <h1>Student Registration Form</h1>
    <form @submit.prevent="fetchRegistration">
      <label for="registrationId">Enter Registration ID:</label>
      <input type="number" v-model.number="registrationId" min="1" required />
      <button type="submit">Search</button>
       <label for="StudentId">Enter Student ID:</label>
      <input type="number" v-model.number="StudentId" min="1" required />
      <button type="submit">Search</button>
    </form>

    <div v-if="loading">Loading...</div>
    <div v-if="error" style="color: red">{{ error }}</div>
    <div v-if="registration">
      <h2>Registration Details</h2>
      <p><strong>Title:</strong> {{ registration.title }}</p>
      <p><strong>Completed:</strong> {{ registration.completed ? 'Yes' : 'No' }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const registrationId = ref(null)
const registration = ref(null)
const loading = ref(false)
const error = ref(null)

 const fetchRegistration = async () => {
    
  if(!registrationId.value) return
  loading.value = true
  error.value = null
  registration.value = null

  try {
    const response = await fetch(`https://jsonplaceholder.typicode.com/todos/${registrationId.value}`)
   
    if (!response.ok) {
      throw new Error('Registration not found')
    }

    const data = await response.json()
    registration.value = data
  } catch (err) {
    error.value = err.message
  } finally {
    loading.value = false
  }
}
</script>
