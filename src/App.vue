<template>
  <div id="app">
    <FormationList />
    <FormationForm />
  </div>
</template>

<script>
import FormationList from './components/FormationList.vue';
import FormationForm from './components/FormationForm.vue';

export default {
  name: 'App',
  components: {
    FormationList,
    FormationForm
  }
};
</script>

<style>
/* Ajoutez du style global si nécessaire */
</style>
