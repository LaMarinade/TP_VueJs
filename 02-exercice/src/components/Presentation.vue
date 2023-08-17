<template>
    <div>
      <label for="name">Nom :</label>
      <input id="name" type="text" v-model="name" />
  
      <label for="age">Âge :</label>
      <input id="age" type="number" v-model="age" />

      <!-- Dans cet exemple, nous avons créé deux données name et age en utilisant ref. Les champs de saisie <input /> sont reliés à ces données en utilisant la directive v-model. Cela signifie que lorsque vous entrez quelque chose dans les champs de saisie, les données name et age seront automatiquement mises à jour en fonction de ce qui est saisi. -->
    
     <!-- Ensuite, nous affichons les valeurs saisies en dessous des champs de saisie en utilisant l'interpolation ({{ ... }}) dans le template. -->

      
      <p>Nom saisi : {{ name }}</p>
      <p>Âge saisi : {{ age }}</p>
      
      <p>Âge dans 10 ans : {{ agePlusTen }}</p>
      <p>Nombre de caractères dans le nom : {{ nameLength }}</p>
      <p>Nom en majuscules : {{ nameUpperCase }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';

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
  </script>
  


  <style scoped>
 div {
 background-color: lightblue;
 font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
 padding: 30px ;
 border-radius: 5px;

}

input{
  border-radius: 5px;
  border : 0;
}
  </style>
  