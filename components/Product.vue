<script setup>
  import ClientReview from "~/components/ClientReview.vue";

  const props = defineProps({
    fullName: String,
    description: String,
    imageUrl: String,
    price: Number,
    priceDescription: String,
    availableProduct: Number,

  })

  const productDescription = computed( ()=> {
    return props.description.replace(/\. /g, '.<br>')
  } )

</script>

<template>
  <div class="product">
    <h2> {{ props.fullName }} </h2>
    <div class="product-content">
      <img :src="props.imageUrl" :alt="props.name">
      <label v-html="productDescription"> </label>
    </div>
    <input type="button" :value="`au prix de ${props.price} €*`" />
    <label class="subTitle">*{{ props.priceDescription }} </label>
  </div>
  <div class="review">
    <ClientReview/>
  </div>

</template>

<style scoped lang="scss">
@use "assets/scss/var.scss" as *;

$imageWidth: 200px;

.product {
  display: flex;
  flex-direction: column;

  margin:  0 25vw;

  width: $imageWidth;

  * {
    margin: 0;
    padding: 10px 0;
  }

  h2 {
    width: fit-content;
    margin: 0 auto;
  }

  p {
    width: $imageWidth;
  }

  label {
    padding: 0;
    white-space: pre-wrap;
  }

  .product-content {
    display: flex;
    flex-direction: row;
    gap: 15px;
    padding: 0;
    width: 600px;
  }

  .subTitle {
    font-size: xx-small;
  }

  input[type=button] {
    width: fit-content;
    margin: 0 auto;
    padding: 10px;

    background-color: $mainColor;
    border: none;
    border-radius: 10px;

    transition: transform 0.3s ease;

    &:hover {
      cursor: pointer;
      background-color: $mainColorVif;
      transform: scale(1.1);
    }
  }

}

.review {
  width: fit-content;
  margin:  0 auto;
}

</style>