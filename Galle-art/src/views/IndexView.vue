<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container">
            <h1 class="title navbar-brand mx-auto">Galle-art</h1>
        </div>
    </nav>

    <div class="d-flex justify-content-start">
        <div class="q-card card p-3 ms-1 mt-1 ">
            <div class="my-3" id="search-bar">
                <input type="text" id="search" placeholder="Buscar usuario">
            </div>

            <div id="filter-section">
                <h2 class="my-3">Filtro</h2>
                <input class="my-3" type="checkbox" id="collection4" name="calificación4">
                <label class="my-3" for="collection4">Mostrar publicaciones calificación 4</label><br>
                <input class="my-3" type="checkbox" id="collection3" name="calificación3">
                <label class="my-3" for="collection3">Mostrar publicaciones calificación 3</label><br>
                <input class="my-3" type="checkbox" id="collection2" name="calificación2">
                <label class="my-3" for="collection2">Mostrar publicaciones calificación 2</label><br>
                <input class="my-3" type="checkbox" id="collection1" name="calificación1">
                <label class="my-3" for="collection1">Mostrar publicaciones calificación 1</label><br>
            </div>
        </div>

        <div class="q-card p-5 ms-3 mt-1">
            <div id="upload-section">
                <h2>Subir nueva publicación</h2>
                <input type="file" id="new-publication" name="new-publication">
            </div>
        </div>

        <div id="upload-section">
            <h2>Subir nueva publicación</h2>
            <input type="file" id="new-publication" name="new-publication" @change="handleFileUpload">
        </div>

        <div id="image-list">
            <img v-for="image in images" :src="image" alt="Uploaded image">
        </div>
    </div>
</template>

<style>
.card {
    width: fit-content;
}

.title {
    font-family: 'knewave';
    color: black;
    font-size: x-large;
}

label,
h2 {
    color: black;
}
</style>

<script>
export default {
    data() {
        return {
            images: [],
        };
    },
    methods: {
        handleFileUpload(event) {
            const file = event.target.files[0];
            const reader = new FileReader();

            reader.onload = (e) => {
                this.images.push(e.target.result);

                const imagesJson = JSON.stringify(this.images);

                localStorage.setItem('images', imagesJson);
            };

            reader.readAsDataURL(file);
        },
    },
    mounted() {
        const imagesJson = localStorage.getItem('images');
        this.images = JSON.parse(imagesJson) || [];
    },
};
</script>