<template>
  <div v-if="product">
    <p>{{ product.title }}</p>
    <p>{{ product.price }}</p>
    <p>{{ product.id }}</p>
  </div>
  <div v-else>
    <p>Loading...</p>
  </div>
</template>

<script setup>
const { id } = useRoute().params

const uri = "https://fakestoreapi.com/products/" + id

const { data: product } = await useFetch(uri, { key: id })
definePageMeta({
  layout: "products",
})
</script>

<style scoped></style>
