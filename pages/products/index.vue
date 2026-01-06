<template>
    <div>Product Page</div>
    <div v-for="p in products" :key="p.id">
        <NuxtLink :to="`/products/${p.id}`">{{ p.title }}</NuxtLink>
    </div>
</template>

<script setup>
    const { data: products } = useFetch('https://fakestoreapi.com/products')
    console.log(products)
</script>