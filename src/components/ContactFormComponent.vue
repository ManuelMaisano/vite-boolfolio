<template>
    <div>
      <h1>Contattaci</h1>
      <form @submit.prevent="sendEmail">
        <div class="mb-3">
          <label for="name" class="form-label">Nome</label>
          <input type="text" class="form-control" id="name" v-model="form.name" required>
        </div>
        <div class="mb-3">
          <label for="email" class="form-label">Email</label>
          <input type="email" class="form-control" id="email" v-model="form.email" required>
        </div>
        <div class="mb-3">
          <label for="message" class="form-label">Messaggio</label>
          <textarea class="form-control" id="message" v-model="form.message" rows="3" required></textarea>
        </div>
        <button type="submit" class="btn btn-primary">Invia</button>
      </form>
    </div>
  </template>

  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        form: {
          name: '',
          email: '',
          message: ''
        },
        success: '',
        error: ''
      };
    },
    methods: {
      async sendEmail() {
        try {
          const response = await axios.post('http://localhost:8000/contact', this.form);
          this.success = 'Email inviata con successo!';
          this.error = '';
          this.form = {
            name: '',
            email: '',
            message: ''
          };
        } catch (error) {
          this.error = 'Si è verificato un errore. Per favore riprova più tardi.';
          this.success = '';
        }
      }
    }
  };
  </script>

  <style scoped>
  /* Aggiungi eventuali stili personalizzati qui */
  </style>