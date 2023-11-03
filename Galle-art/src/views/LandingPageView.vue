
import { RouterLink } from 'vue-router';
<template>
    <div class="image">
        <img src="../assets/images/painting-3995999_1920.jpg" alt="landing page image">
        <h1 class="title">Galle-art</h1>
        <p class="description">Un espacio para el arte, un lugar para mostrar tus obras a los demás.</p>
        <RouterLink class="button" to="/login" >Empieza ya</RouterLink>
        <div class="foot"></div>
    </div>
</template>

<style scoped>
.image {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}

.image img {
  min-width: 100%;
  min-height: 100%;
}

.title{
    position: absolute;
    font-family: 'knewave';
    font-size: 150px;
    color: azure;
    margin-top: -400px;
}

.description{
    position: absolute;
    font-family: 'jaldi';
    font-size: 35px;
    color: azure;
}

.button{
  position: absolute;
  background-color: aliceblue;
  margin-bottom: -450px;
  padding-left: 70px;
  padding-right: 70px;
  padding-top: 30px;
  padding-bottom: 30px;
  font-size: larger;
  font-family: 'jaldi' !important;
  color: black;
  border-radius: 10px;
  z-index: 1;
  text-decoration: none;
}

.button:hover{
  color: aliceblue;
  background-color: rgb(92, 92, 92);
}

.foot{
  position: absolute;
  bottom: 0;
  background-color: white;
  width: 100%;
  height: 274px;
  opacity: 60%;
}
</style>