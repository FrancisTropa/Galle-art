<template>
    <form class="card p-5 ms-5 my-5 d-flex flex-column text-center">
        <div v-if="errorMessage" class="alert alert-danger" role="alert">
            {{ errorMessage }}
        </div>
        <div class="mb-3 col-7 py-3 mx-auto flex-grow-1 flex-lg-grow-0 vh-50 vh-lg-100">
            <label for="e-mail" class="form-label">Ingese su correo</label>
            <input type="email" v-model="email" name="correo" id="e-mail" class="form-control">
        </div>
        <div class="mb-3 col-7 py-3 mx-auto flex-grow-1 flex-lg-grow-0 vh-50 vh-lg-100">
            <label for="pass" class="form-label">Ingese su contraseña</label>
            <input type="password" v-model="password" name="contraseña" id="pass" class="form-control">
        </div>
        <div class="d-grid gap-2 col-5 mx-auto flex-grow-1 flex-lg-grow-0 vh-50 vh-lg-100">
            <button class="btn btn-primary" type="button" @click="login">Iniciar sesión</button>
        </div>
        <div class="d-flex justify-content-center align-items-center mt-4">
            <p class="mb-0">¿No tiene cuenta?</p>
            <router-link to="/register" class="ms-2">Registrese</router-link>
        </div>
    </form>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      errorMessage: '',
    };
  },
  methods: {
    login() {
      if (!this.email || !this.password) {
        this.errorMessage = 'Por favor, rellena todos los campos.';
      } else {
        const userJson = localStorage.getItem('user');
        const user = JSON.parse(userJson);

        if (user.email === this.email && user.password === this.password) {
          this.$router.push('/index');
        } else {
          this.errorMessage = 'Correo electrónico o contraseña incorrectos. Por favor, inténtalo de nuevo.';
        }
      }
    },
  },
};
</script>

<style scoped>
router-link{
    color: rgb(59, 134, 233) !important;
}
</style>