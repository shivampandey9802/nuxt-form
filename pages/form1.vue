<template>
    <div>Home</div>
    <form @submit.prevent="handleSubmit" flex>
        <div v-for="type in types" :key="type.type">
            <label for="">{{ type.label }}: </label>
            <input :type="type.type" v-model="formData[type.label]">
        </div>
        <button type="submit">Submit</button>
    </form>
</template>

<script setup>
    const types = ref([{type:'text', label: 'name'}, {type:'email', label:'email'}, {type:'password', label:"password"}, {type:'checkbox', label:'skill'}, {type:'radio', label: 'gender'}])
    const formData = ref({
        name:'shivam',
        password: '',
        email: '',
        checkbox: false,
        // radio: true
    })
    const handleSubmit = () => {
        console.log(formData.value)
    }
</script>

<style>

</style>

