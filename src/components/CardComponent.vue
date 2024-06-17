<template>
    <div class="card mb-3">
      <div class="card-body">
        <h5 class="card-title">{{ project.title }}</h5>
        <p class="card-text">{{ project.content }}</p>
        <p class="card-text"><small class="text-muted">Tipologia: {{ project.type ? project.type.name : 'Nessuna' }}</small></p>
        <p class="card-text">
          <small class="text-muted">Tecnologie: 
            <span v-if="project.technologies.length > 0">
              <span v-for="technology in project.technologies" :key="technology.id">
                {{ technology.name }}
              </span>
            </span>
            <span v-else>
              Nessuna tecnologia
            </span>
          </small>
        </p>
      </div>
    </div>
  </template>

  <script>
  export default {
    name: 'CardComponent',
    props: {
      project: {
        type: Object,
        required: true
      }
    }
  };
  </script>

  <style scoped>
  
  </style>