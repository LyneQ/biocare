<script setup>
const props = defineProps({
  newsTitle: String,
  newsDate: String,
  newsImage: String,
  newsID: Number,
})
</script>

<template>
  <div class="card">
      <img :src=newsImage height="150" alt="Article"/>
      <h5 class="news-date"> {{ props.newsDate }} </h5>
      <h3 class="news-title"> {{ props.newsTitle }}  </h3>
      <NuxtLink :to="`/news/${props.newsID}`">en savoir plus</NuxtLink>
  </div>
</template>

<style scoped lang="scss">
@use "assets/scss/var.scss" as *;
  .card {
    margin: 10px;
    display: inline-flex;
    flex-direction: column;
    flex-wrap: nowrap;
    *{
      margin: 0;
      text-align: left !important;
      max-width: 300px;
    }

    .news-date {
      margin: 15px 0 5px 0;
    }

    .news-title {
      margin: 0 0 10px 0;
    }
  }
</style>