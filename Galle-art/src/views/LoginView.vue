<template>
    <div class="d-flex vh-100">
      <div class=" vh-100">
        <img src="../assets/images/watercolor-2681039_1280.jpg" alt="cover image" class="img-fluid h-100">
      </div>
      <div class="w-50 mt-5">
        <h1 class="title display-4 mx-auto mb-5 text-center">Galle-art</h1>
        <Login />
      </div>
    </div>
</template>

<script>
  import Login from '../components/Login.vue'
  
  export default {
    components: {
      Login
    }
  }
</script>

<style scoped>
    .title{
        font-family: 'knewave';
        color: black;
    }
</style>