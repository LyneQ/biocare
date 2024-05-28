<script setup>
import products from "../assets/json/products.json"
</script>

<template>
  <section class="content">
    <div v-for="product in products.data" :key="product.id" class="test">
      <Product
        :full-name="product.name"
        :description="product.description"
        :image-url="product.imageUrl"
        :price="product.price"
        :priceDescription="product.priceDescription"
        :available-product="product.availableProduct"
      />
    </div>
  </section>
</template>

<style scoped lang="scss">

.content {
  width: 100% !important;
  display: block;
  margin-left: auto;
  margin-right: auto;

  &:only-child {
    width: fit-content;
  }
}


</style>