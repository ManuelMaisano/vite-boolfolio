<template>
 <div id="app">
  <HeaderComponent></HeaderComponent>
    <h1>Progetti</h1>
    <ul>
      <li v-for="project in projects" :key="project.id">
        {{ project.title }}
      </li>
    </ul>
  </div>
</template>

<script>
 import axios from 'axios';
 import HeaderComponent from './components/HeaderComponent.vue';
export default {
  name: 'App',
  components: {
    HeaderComponent
  },
  data() {
    return {
      projects: []
    };
  },
  created() {
    axios.get('http://localhost:8000/api/projects')
      .then(response => {
        this.projects = response.data;
        console.log(response.data);
      })
      .catch(error => {
        console.error('Error fetching projects:', error);
      });
  }
};

<style lang="scss" scoped>

</style>