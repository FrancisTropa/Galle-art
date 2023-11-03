<template>
    <form class="card p-5 ms-5 my-5 d-flex flex-column text-center">
        <div class="mb-3 col-7 py-3 mx-auto flex-grow-1 flex-lg-grow-0 vh-50 vh-lg-100">
            <label for="e-mail" class="form-label">Ingese su correo</label>
            <input type="email" name="correo" id="e-mail" class="form-control">
        </div>
        <div class="mb-3 col-7 py-3 mx-auto flex-grow-1 flex-lg-grow-0 vh-50 vh-lg-100">
            <label for="pass" class="form-label">Ingese su contraseña</label>
            <input type="password" name="contraseña" id="pass" class="form-control">
        </div>
        <div class="d-grid gap-2 col-5 mx-auto flex-grow-1 flex-lg-grow-0 vh-50 vh-lg-100">
            <button class="btn btn-primary" type="button">Iniciar sesión</button>
        </div>
        <div class="d-flex justify-content-center align-items-center mt-4">
            <p class="mb-0">¿No tiene cuenta?</p>
            <router-link to="/register" class="ms-2">Registrese</router-link>
        </div>
    </form>
</template>

<style scoped>
router-link{
    color: rgb(59, 134, 233) !important;
}
</style>