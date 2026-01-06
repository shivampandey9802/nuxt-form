<template>
  <div>
    <h2>Step 1</h2>

    <input v-model="formData.name" placeholder="Name" required>/>
    <input v-model="formData.email" placeholder="Email" required>/>

    <button @click="$emit('next')">Next</button>
  </div>
</template>

<script setup>
defineProps({
  formData: Object
})
</script>
