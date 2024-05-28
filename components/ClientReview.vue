<script setup>
const avisClient = [
  {
    fullName: "stéphanie delangle",
    stars: 4,
    review: "EnerBoost m'a vraiment aidée à surmonter ma fatigue chronique. Je me sens beaucoup plus énergique tout au long de la journée et ma concentration s'est nettement améliorée."
  },
  {
    fullName: "julien martin",
    stars: 5,
    review: "Ce médicament est incroyable! Depuis que j'utilise EnerBoost, ma productivité a doublé et je ne ressens plus cette fatigue constante. Je le recommande vivement."
  },
  {
    fullName: "marie dupont",
    stars: 3,
    review: "fonctionne bien pour améliorer ma concentration, mais je ressens encore un peu de fatigue en fin de journée. C'est un bon produit, mais pas parfait."
  },
  {
    fullName: "lucas bernard",
    stars: 2,
    review: "Je n'ai pas remarqué de grande différence avec EnerBoost. Ma fatigue est toujours présente, même si ma concentration semble légèrement meilleure."
  },
  {
    fullName: "emma leroy",
    stars: 4,
    review: "ça a vraiment changé ma routine quotidienne. Je suis plus alerte et concentrée, et la fatigue ne m'accable plus comme avant. Un excellent produit!"
  },
  {
    fullName: "antoine simon",
    stars: 1,
    review: "Malheureusement, ça n'a pas eu l'effet escompté pour moi. Je ne ressens aucune amélioration significative ni en termes d'énergie ni de concentration."
  },
  {
    fullName: "Jane Doe",
    stars: 5,
    review: "EnerBoost est un produit révolutionnaire! Je me sens revitalisée et ma capacité de concentration est à son maximum. Je suis très satisfaite des résultats."
  }
];

</script>

<template>
  <hr style="width: 80vw; margin: 5vh auto 0;"/>
<section class="review-list">
  <div class="review" v-for=" review in avisClient">
    <h3> {{ review.fullName }} </h3>
    <span v-for=" i in review.stars">
      <img src="/star-solid.svg" :style="[ i == 1 ? 'padding-left: 10px;' : null ]" class="star" alt="étoile de notation" width="25" draggable="false"/>
    </span>
    <p> {{ review.review }} </p>
  </div>
</section>


</template>

<style scoped lang="scss">
@use "assets/scss/var.scss" as *;

  * {
    margin: 0;
    padding: 0 10px;
  }

  .review-list {
    width: 80vw;
    margin-top: 20px;

    display: inline-flex;
    flex-direction: row;
    flex-wrap: wrap;
    //justify-content: center;
    align-items: stretch;
    gap: 10px;

  }

  .review {
    width: 300px;

    padding: 10px;

    border: 1px solid $fontColor;
    border-radius: 10px;

    .star, span {
      padding: 0;
      width: 25px;


    }

  }
</style>