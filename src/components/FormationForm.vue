<template>
  <div>
    <h1>Inscription à une Formation</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="name">Nom :</label>
        <input type="text" id="name" v-model="name" required>
      </div>
      <div>
        <label for="email">Email :</label>
        <input type="email" id="email" v-model="email" required>
      </div>
      <div>
        <label for="formation">Formation :</label>
        <select id="formation" v-model="formation" required>
          <option value="" disabled selected>Choisissez une formation</option>
          <option v-for="formation in formations" :key="formation.id" :value="formation.id">
            {{ formation.name }} - {{ formation.description }}
          </option>
        </select>
      </div>
      <button type="submit">S'inscrire</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      name: '',
      email: '',
      formation: '',
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
  },
  methods: {
    submitForm() {
      const registrationData = {
        name: this.name,
        email: this.email,
        formation: this.formation
      };
      axios.post('https://api.example.com/inscriptions', registrationData)
        .then(response => {
          alert('Inscription réussie !');
          this.name = '';
          this.email = '';
          this.formation = '';
        })
        .catch(error => {
          console.error('There was an error submitting the form!', error);
        });
    }
  }
};
</script>

<style scoped>
/* Ajoutez du style si nécessaire */
</style>

  