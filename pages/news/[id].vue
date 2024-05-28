<script setup>
import newsJson from "../../assets/json/news.json"
const route = useRoute()

const article = ref( newsJson.news.index.find( (el) => el.id === parseInt( route.params.id ) ) );
const articleContent = article.value.content;
</script>

<template>
  <section>
    <div class="news-content" >
      <h2 class="title">
        {{ article['long-title'] }}
      </h2>
      <div v-for="(data, index) in articleContent">
        <p :class="index === 0 ? null : 'news-format' " >
          {{ data }}
        </p>
        <img v-show=" index === 0" :src="article['large-icon-url']" :alt="article['short-title']"/>
      </div>
    </div>
</section>
</template>

<style scoped>

img {
  padding: 10px;
  width: 40vw;
}

section {
  margin: 0 120px;
}

.title {
  width: fit-content;
  margin: 20px auto;
}

.news-content{
  font-family: "Montserrat", sans-serif;

  margin: 10px auto;
  width: 40vw;

  p {
    width: 100%;
    margin: 0;
  }

  .news-format {
    margin: 10px auto;
  }


}

</style>