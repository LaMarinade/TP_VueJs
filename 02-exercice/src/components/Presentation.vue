<!-- -----------------------------CONTENU/TEMPLATE----------------------------- -->

<template>
    <div class="presentation-container">
        <div class="input-container">
      <label for="name">Nom :</label>
      <input id="name" type="text" v-model="name" :class="{ 'input-error': isNameInvalid }" />
  
      <label for="age">Âge :</label>
      <input id="age" type="number" v-model="age" :class="{ 'input-error': isAgeInvalid }" />
      
      <button class="btn-random" @click="generateRandomPerson">Générer une personne aléatoire</button>
    

      <p v-if="isNameTooLong">Le nom ne doit pas dépasser 15 caractères.</p>
        <p v-if="isAgeOutOfRange">L'âge doit être compris entre 1 et 100 ans.</p>
    
    <p v-show="isValid" class="valid-message">Données valides.</p>
    <p v-show="!isValid" class="error-message">Veuillez entrer un prénom et un page valide !</p>
        </div>
      <!-- Dans cet exemple, nous avons créé deux données name et age en utilisant ref. Les champs de saisie <input /> sont reliés à ces données en utilisant la directive v-model. Cela signifie que lorsque vous entrez quelque chose dans les champs de saisie, les données name et age seront automatiquement mises à jour en fonction de ce qui est saisi. -->
    
     <!-- Ensuite, nous affichons les valeurs saisies en dessous des champs de saisie en utilisant l'interpolation ({{ ... }}) dans le template. -->

     <div class="message-container">
      
      <p>Nom saisi : {{ name }}</p>
      <p>Âge saisi : {{ age }}</p>
      
      <p>Âge dans 10 ans : {{ agePlusTen }}</p>
      <p>Nombre de caractères dans le nom : {{ nameLength }}</p>
      <p>Nom en majuscules : {{ nameUpperCase }}</p>

      </div>

    
</div>
  </template>


<!-- -----------------------------SCRIPT----------------------------- -->

  
  <script setup>
  import { ref, computed, onMounted } from 'vue';

  // import { ref } from 'vue';: Cette ligne importe la fonction ref de la bibliothèque Vue. ref est une fonction qui vous permet de créer une variable réactive. Cela signifie que chaque fois que la valeur de cette variable change, les parties du code qui en dépendent sont automatiquement mises à jour.

  
  const name = ref('');
  const age = ref(0);
  
  const agePlusTen = computed(() => {
    return age.value + 10;
  });
  
  const nameLength = computed(() => {
    return name.value.length;
  });
  
  const nameUpperCase = computed(() => {
    return name.value.toUpperCase();
  });

  const isNameTooLong = computed(() => name.value.length > 15);
  const isAgeOutOfRange = computed(() => age.value < 1 || age.value > 100);

  const isNameInvalid = computed(() => isNameTooLong.value);
  const isAgeInvalid = computed(() => isAgeOutOfRange.value);

  const isValid = computed(() => !isNameInvalid.value && !isAgeInvalid.value);
  
  const names = ['Alice', 'Bob', 'Charlie', 'David', 'Emma', 'Fiona', 'George', 'Hannah'];
 const getRandomName = () => names[Math.floor(Math.random() * names.length)];


function getRandomAge() {
  return Math.floor(Math.random() * 100) + 1;
}

 function generateRandomPerson() {
  name.value = getRandomName();
  age.value = getRandomAge();
}

onMounted(generateRandomPerson);

  </script>
  

<!-- -----------------------------STYLE----------------------------- -->

  <style scoped>

body{
    
}  

.presentation-container{
     font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }
 .input-container {
 background-color: lightblue;
 padding: 30px ;
 border-radius: 5px;
 min-width: 50%;

}

.message-container{
    padding: 30px ;
    border-radius: 5px;
    background-color: aquamarine;
    margin-top: 1rem;
}

input{
  border-radius: 5px;
  border : 0;
}

.input-error {
  border: 1px solid red;
  background-color: #ffeeee;
}

.error-message {
  color: red;
}
.valid-message {
  color: rgb(65, 177, 59);
}

.btn-random{
    border-radius: 5px;
    cursor: pointer;
    margin-left: 1rem;
}
  </style>
  