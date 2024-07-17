<template>
    <div>
      <h1>Liste des Formations</h1>
      <ul>
        <li v-for="formation in formations" :key="formation.id">
          {{ formation.name }} - {{ formation.description }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        formations: []
      };
    },
    mounted() {
      axios.get('https://api.example.com/formations')
        .then(response => {
          this.formations = response.data;
        })
        .catch(error => {
          console.error('There was an error fetching the formations!', error);
        });
    }
  };
  </script>
  
  <style scoped>
  /* Ajoutez du style si nécessaire */
  </style>
  