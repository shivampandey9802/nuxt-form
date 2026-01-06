<template>
  <div>
    <h2>Step 1</h2>

    <input v-model="formData.name" placeholder="Name" />
    <input v-model="formData.email" placeholder="Email" />

    <button @click="$emit('next')">Next</button>
  </div>
</template>

<script setup>
defineProps({
  formData: Object
})
</script>
