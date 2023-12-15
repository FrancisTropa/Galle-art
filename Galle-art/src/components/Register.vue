<template>
    <form class="card p-5 ms-5 my-5 d-flex flex-column text-center" @submit.prevent="register">
        <div v-if="errorMessage" class="alert alert-danger" role="alert">
            {{ errorMessage }}
        </div>
        <div class="mb-3 col-7 py-3 mx-auto flex-grow-1 flex-lg-grow-0 vh-50 vh-lg-100">
            <label for="username" class="form-label">Ingese su nombre de usuario</label>
            <input v-model="username" type="text" name="username" id="username" class="form-control">
        </div>
        <div class="mb-3 col-7 py-3 mx-auto flex-grow-1 flex-lg-grow-0 vh-50 vh-lg-100">
            <label for="e-mail" class="form-label">Ingese su correo</label>
            <input v-model="email" type="email" name="correo" id="e-mail" class="form-control">
        </div>
        <div class="mb-3 col-7 py-3 mx-auto flex-grow-1 flex-lg-grow-0 vh-50 vh-lg-100">
            <label for="pass" class="form-label">Ingese su contraseña</label>
            <input v-model="password" type="password" name="contraseña" id="pass" class="form-control">
        </div>
        <div class="d-grid gap-2 col-5 mx-auto flex-grow-1 flex-lg-grow-0 vh-50 vh-lg-100">
            <button class="btn btn-primary" type="submit">Registrar</button>
        </div>
    </form>
</template>
  
<script>
import axios from 'axios';

export default {
  data() {
    return {
      username: '',
      email: '',
      password: '',
      errorMessage: '',
    };
  },
  methods: {
    async register() {
      if (!this.username || !this.email || !this.password) {
        this.errorMessage = 'Por favor, rellena todos los campos.';
      } else {
        try {
          await axios.post('http://localhost:3000/auth/register', {
            name: this.username,
            email: this.email,
            password: this.password,
          });

          // Redirigir al usuario a la página de inicio de sesión
          this.$router.push('/login');
        } catch (error) {
          this.errorMessage = 'Hubo un error al crear tu cuenta. Por favor, inténtalo de nuevo.';
        }
      }
    },
  },
};
</script>