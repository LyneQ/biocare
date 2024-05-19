<script setup>
import newsJson from "../../assets/json/news.json"
const route = useRoute()

const article = ref( newsJson.news.index.find( (el) => el.id === parseInt( route.params.id ) ) );
const articleContent = article.value.content;
</script>

<template>
<section>
    <h2 class="title">
      {{ article['long-title'] }}
    </h2>
    <div class="news-header">
    </div>
    <div class="news-content" >
      <div v-for="(data, index) in articleContent">
        <img v-show=" index === 0" :src="article['large-icon-url']" :alt="article['short-title']"/>
        <p :class="index === 0 ? null : 'news-format' " >
          {{ data }}
        </p>
      </div>
    </div>
</section>
</template>

<style scoped>

img {
  min-width: 500px;
  max-height: 400px;
}

section {
  margin: 0 120px;
}

.news-content{

  width: 75vw;

  p {
    width: 100%;
    margin: 0;
  }

  .news-format {
    margin: 20px auto;
  }

  :first-child {
    display: inline-flex;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: normal;
    gap: 15px;
  }
}

</style>