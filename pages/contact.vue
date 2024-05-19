<script setup>
import ContactForm from "~/components/ContactForm.vue";

</script>
<template>
    <div class="section-form">
      <div class="contact-information">
        <h1> contacter BioCare </h1>
        <p>
          L'équipe de BioCare Inc. s'engage à répondre à vos demandes dans les meilleurs délais.
          <br/>
          Votre satisfaction est notre priorité.
        </p>
      </div>
      <ContactForm/>
    </div>
</template>

<style scoped>

.section-form {

  padding-top: 15vh;

  min-height: 83vh;
  font-size: large;
  display: flex;
  flex-direction: row;
  justify-content: center;

  color: white;
  /**
  * changer le background
  */
  background-image: url("/sebastian Unrau- forest.jpg");
  background-position-y: bottom;
}
.contact-information {
  min-width: fit-content;
  p {
    width: 25vw;
  }
}

</style>