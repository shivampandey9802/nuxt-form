<template>
  <div>
    <h2>Step 3</h2>

    <input v-model="formData.address" placeholder="Address" />

    <button @click="$emit('prev')">Back</button>
    <button @click="$emit('submit')">Submit</button>
  </div>
</template>

<script setup>
defineProps({
  formData: Object
})
</script>
