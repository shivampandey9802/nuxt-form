<template>
  <div>
    <h2>Step 2</h2>

    <input type="number" v-model="formData.age" placeholder="Age" required>

    <button @click="$emit('prev')">Back</button>
    <button @click="$emit('next')">Next</button>
  </div>
</template>

<script setup>
defineProps({
  formData: Object
})
</script>
