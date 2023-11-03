<template>
    <div class="auth-layout">
      <div class="image">
        <img src="../assets/images/watercolor-2681039_1280.jpg" alt="cover image">
      </div>
      <div class="form-container">
        <h1 class="title">Galle-art</h1>
        <div>
          <slot></slot>
        </div>
      </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Jaldi&family=Knewave&family=Roboto+Mono&display=swap');
.title{
    font-family: 'knewave' !important;
    font-size: 100px;
    color: black;
}

.image {
  position: relative;
  width: 50vw;
  height: 100vh;
  overflow: hidden;
}

.image img {
  position: absolute;
  min-width: 100%;
  min-height: 100%;
  margin-top: -200px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  flex: 1;
}

.form-container {
    background-color: aliceblue;
    flex-grow: 1;
}

.auth-layout {
  display: flex;
}
</style>