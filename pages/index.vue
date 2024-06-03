<script setup>
// some code here
import newsJson from "../assets/json/news.json"
const news = ref(newsJson.news.index);


</script>

<template>
  <section class="main">
    <h1 class="title"> Qui sommes-nous ? </h1>
    <div class="content">
      <img src="/wafton.png" alt="photo d'une de nos équipe (463)"/>
      <p>
        Nous sommes BioCare, une société pharmaceutique basée au Listembourg, créée par DR W. Afton.
        <br/>
        Notre mission est d'améliorer votre condition de vie à travers nos produits révolutionnaires,
        dans l'espoir de vous rendre votre vitalité d'antan. Nos recherches incessantes et notre engagement envers l'innovation
        nous ont permis de développer une gamme de produits à la pointe de la technologie,
        tous conçus pour répondre à vos besoins de manière sûre et efficace. Chez BioCare,
        nous croyons en une approche holistique de la santé, en mettant l'accent sur la prévention autant que sur le traitement.
        <br/>
        Chaque jour, notre équipe dévouée de chercheurs, scientifiques et professionnels de la santé travaille sans relâche pour
        offrir des solutions novatrices et adaptées à vos besoins individuels. Avec BioCare, vous pouvez avoir confiance en une
        qualité inégalée et une passion constante pour votre bien-être. Nous sommes là pour vous accompagner à chaque étape de votre
        parcours vers une vie plus saine et plus épanouie.
      </p>
    </div>
    <section class="news">
      <div class="news-Header">
        <h2>
          les dernières nouvelles
        </h2>
        <p>
          Les dernières nouvelles et recherches de l'équipe de BioCare.<br/>
          Tenez-vous au courant de nos actualités.
        </p>
      </div>
      <div class="content" v-for="article in news" :key="article.id">
        <NewsCard :news-date="article.creationDate"
                  :news-image="article['icon-url']"
                  :news-title="article['short-title']"
                  :news-i-d="article.id"
        />
      </div>
    </section>
  </section>
</template>
<style scoped>

.main {
  margin: 0 auto;
  padding: 0 120px;
}

.title {
  text-align: center ;
}
.content {
  display: inline-flex;
  flex-direction: row;
  justify-content: center;
  flex-wrap: nowrap;
  align-items: flex-start;

  img {
    width: 500px;
  }

  p {
    margin: 0 30px;

    width: 40%;
  }
}

.news {
  width: fit-content;
  margin-left: auto;
  margin-right: auto;
  padding: 0;
}

.news-Header {
  margin-left: 10px;
}

</style>