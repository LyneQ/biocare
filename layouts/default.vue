<script setup>
useHead({
  title: `BioCare Inc`,
  // meta: [ { name: 'description', content: 'biocare' } ],
})
</script>

<template>
  <div class="container">
    <nav>
      <img src="/banner.png" class="logo" alt="logo de BioCare"/>
      <NuxtLink to="/">Accueil</NuxtLink>
      <NuxtLink to="/nos-soins">nos soins</NuxtLink>
      <NuxtLink to="/contact">page de contact</NuxtLink>
    </nav>
    <div class="main">
      <slot />
    </div>
    <footer>
      <p> <span> © 2024 All rights reserved. </span> BioCare reconnaît les possibles effets indésirables de certains produits.</p>
    </footer>
  </div>
</template>
<style scoped lang="scss">
@use "assets/scss/var.scss" as *;
  nav {
    width: 100%;

    display: inline-flex;
    vertical-align: middle;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: center;

    border-bottom: 2px solid $backgroundColor;
    .logo {
      width: 92px;
    }
    * {
      padding: 10px;
    }
  }

  .container {
    position: relative;
    min-height: 98vh;
  }

  .main {
    padding-bottom: 1rem !important;
  }

  footer{
    position: absolute;
    bottom: -20px;
    width: 100%;
    height: 2.5rem;
    background-color: $backgroundColorLighter;

    border-top: 2px solid $backgroundColor;
    text-align: center;

  }
</style>