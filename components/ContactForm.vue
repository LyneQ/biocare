<script setup>
/**
 * contient les données stockées dans les inputs
 * @type {ModelRef<unknown | undefined, string>}
 */
const firstName= defineModel('firstname', { initial: '' });
const lastName = defineModel('lastname', { initial: '' });
const email = defineModel('email', { initial: '' });
const description = defineModel('description', { initial: '' });

const inputs = reactive({
  firstName : firstName ,
  lastName : lastName ,
  email : email ,
  description : description
})

const inputIsValid = () => {
  let checks = 0;
  let amountOfInputs = 0 ;
  for (let inputsKey in inputs) {
    amountOfInputs++
    const inputData = inputs[inputsKey];
    
    if ( !inputData ) return ;
    switch ( inputsKey ) {
      case 'firstName' :
        if ( inputData ) checks++
        break;
      case 'lastName':
        if ( inputData ) checks++
        break;
      case 'email':
        if ( inputData && inputData.indexOf('@') !== -1 ) checks++
        break;
      case 'description':
        if ( inputData && inputData.length >= 15 ) checks++
        break;
    }
  }
  return (checks === amountOfInputs)  && ( checks !== 0 )
}

const submitForm = () => {
  if ( inputIsValid() ) {
    alert(`merci ${inputs.lastName} ${inputs.firstName}, votre message nous a été transmis avec succès`)
  } else {
    alert('Veuillez remplir tout les champs de texte ayant une petite étoile');
  }
}
</script>

<template>
  <form @submit="submitForm">
    <div id="form-name">
      <div class="field">
        <label>Votre prénom *</label>
        <input v-model="firstName" type="text" >
      </div>
      <div class="field">
        <label>Votre nom de famille *</label>
        <input v-model="lastName" type="text" >
      </div>
    </div>
    <label>Votre e-mail *</label>
    <input v-model="email" type="email" >
    <label>Description *</label>
    <textarea v-model="description" rows="5" ></textarea>

    <input type="submit" class="button" value="envoyer">
  </form>
</template>

<style scoped lang="scss">
@use "assets/scss/var.scss" as *;
* {
  font-size: large;
  color: white;
  caret-color: white;
}

label {
  font-family: "Raleway", sans-serif;

  text-transform: uppercase;
  margin-top: 10px;
  padding: 10px 0 0 0 !important;
  font-size: x-small;

}

input, textarea {
  border: 1px solid white;
  background-color: transparent;

  resize: none;
}

label, input, textarea {
  margin: 0 10px;
  padding: 10px;
}

form {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  align-content: space-around;
  color: white;

  width: fit-content;

  ::placeholder {
    color: white;
    opacity: 0.90;
  }

}
#form-name {
  display: inline-flex;
}
.field {
  display: flex;
  flex-direction: column;
}

// !button

.button {
  background-color: $mainColor;
  border-radius: 8px;
  border-style: none;
  color: #FFFFFF;
  cursor: pointer;
  display: inline-block;
  margin: 10px 0 0 10px !important;
  padding: 10px 16px;
  width: fit-content;
}

.button:hover,
.button:focus {
  background-color: $mainColorVif;
}
</style>