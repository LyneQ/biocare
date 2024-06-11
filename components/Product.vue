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

  let selector = reactive( {
    description : false,
    review      : false
  })

  const selectorState = (option) => {
    console.log("selector state trigger")
    switch (option) {
      case "description":
        selector.description = !selector.description
        break;
      case "review":
        selector.review = !selector.review
        break;
      default:
        console.log(`choice ${option} not found`);
        break;
    }
  }

</script>

<template>
  <div class="panel">
    <div class="product">
      <h2> {{ props.fullName }} </h2>
      <!-- image and selector -->
      <div class="product-content">
        <img :src="props.imageUrl" :alt="props.name" >
<!--              <label v-html="productDescription"> </label>-->
      </div>
      <input type="button" :value="`au prix de ${props.price} €*`" />
      <label class="subTitle">*{{ props.priceDescription }} </label>
    </div>
    <!-- selector -->
    <div class="product-selector-option">
      <!-- description -->
      <div class="selector-title" @click="selectorState('description')">
      <h4>Description</h4>
        <i v-show="!selector.description" class="fi fi-rr-arrow-small-down"></i>
        <i v-show="selector.description"  class="fi fi-rr-arrow-small-up"></i>
      </div>
      <div v-show="selector.description" class="description" v-html="productDescription">
      </div>
      <!-- review -->
      <div class="selector-title" @click="selectorState('review')">
        <h4>avis client</h4>
        <i v-show="!selector.review" class="fi fi-rr-arrow-small-down"></i>
        <i v-show="selector.review"  class="fi fi-rr-arrow-small-up"></i>
      </div>
      <div v-show="selector.review" class="reviews">
        <ClientReview/>
      </div>
    </div>
  </div>



</template>

<style scoped lang="scss">
@use "assets/scss/var.scss" as *;

$imageWidth: 200px;

img {
  width: $imageWidth;

}

.product {
  display: flex;
  flex-direction: column;

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
    padding-top: 5px;
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
.panel {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  gap: 10px;
  margin:  0 0 0 25vw;

}

.product-selector-option {
  margin-top: 60px;

  width: 400px;

  h4 {
    cursor: pointer;
    width: 400px;

    margin: 0;
    padding: 10px 0;
  }

  .selector-title {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    align-items: center;
    justify-content: space-between;

    border-bottom: 1px solid darkgray;


    -webkit-user-select: none; /* Safari */
    -ms-user-select: none; /* IE 10 and IE 11 */
    user-select: none; /* Standard syntax */

  }

  .description, .review {
      padding-left: 15px;
    }
}

</style>