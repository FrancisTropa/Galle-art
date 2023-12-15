<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container">
            <h1 class="title navbar-brand mx-auto">Galle-art</h1>
        </div>
    </nav>

    <div class="d-flex flex-row">
        <div class="card p-3 ms-1 mt-1 ">
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

        <div class="d-flex flex-column">
            <div class="q-card p-5 ms-3 mt-1">
                <h2>Subir nueva publicación</h2>
                <input type="file" id="new-publication" name="new-publication" ref="fileInput">
                <button @click="handleFileUpload">Subir imagen</button>
                <p v-if="uploading">Subiendo imagen...</p>
            </div>

            <div class="q-card mx-3" id="image-list">
                <div v-for="image in images">
                    <img :src="image.artwork" alt="Uploaded image">
                    <button @click="deleteArtWork(image._id)">Borrar</button>
                </div>
            </div>
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

.q-card{
    width: calc(100% - 40px);
    margin: 40px;
}

.d-flex {
    display: flex;
}

.flex-row {
    flex-direction: row;
}

.flex-column {
    flex-direction: column;
}

.d-flex.flex-column {
    flex-grow: 1;
}

.d-flex.flex-column > .q-card {
    flex-grow: 1;
}

label,
h2 {
    color: black;
}
</style>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            images: [],
            uploading: false,
        };
    },
    methods: {
        async handleFileUpload() {
            const file = this.$refs.fileInput.files[0];
            if (!file) {
                return;
            }

            this.uploading = true;

            const formData = new FormData();
            formData.append('image', file);

            const response = await axios.post('/artWorks', formData, {
                headers: {
                    'Content-Type': 'multipart/form-data'
                }
            });

            this.images.push(response.data.artwork);
            this.uploading = false;
        },
        async deleteArtWork(id) {
            await axios.delete(`/artWorks/${id}`);
            this.images = this.images.filter(image => image._id !== id);
        },
    },
    async mounted() {
        const response = await axios.get('/artWorks');
        this.images = response.data.artworks;
    },
};
</script>