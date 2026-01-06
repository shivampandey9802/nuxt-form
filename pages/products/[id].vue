<template>
    <div>
        <h1>Product id:  {{ id }}</h1>
        <h1>Product name:  {{ product.title }}</h1>
        <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Nisi, voluptatibus!</p>
    </div>
</template>

<script setup>
    const { id } = useRoute().params

    const uri = 'https://fakestoreapi.com/products/' + id
    const { data: product } = useFetch(uri, { key: id})
    console.log('shivam');
    
    console.log(product)

    // const name = ref('dermatouch')
</script>

