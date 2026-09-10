<script setup>
import axios from 'axios';
import { useRoute, useRouter } from 'vue-router';
import { ref } from 'vue';


const route = useRoute();
const poke = ref({});
const router = useRouter();
const back = () => {
    router.back();
}

const getData = async () => {
    try {
        const response = await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
        console.log(response.data);
        poke.value = response.data;
    }
    catch (error) {
        console.log(error);
    }
}
getData();
</script>
<template>
    <div class="container d-flex justify-content-center align-items-center my-5">
        <div class="card border-0 shadow-sm rounded-4 p-4 text-center bg-body" style="max-width: 20rem; width: 100%;">
            <div class="card-body px-0 pt-0">
                <span class="text-muted small fw-medium text-uppercase">Pokémon</span>
                <h4 class="card-title fw-bold text-dark mt-1 mb-3">{{ $route.params.name.toString().toUpperCase() }}
                </h4>
            </div>

            <div class="d-flex justify-content-center my-2">
                <img :src="poke.sprites?.front_default" alt="Pokemon Image" class="img-fluid"
                    style="width: 140px; height: 140px; object-fit: contain;" />
            </div>

            <div class="card-body px-0 pb-0 mt-3">
                <button class="btn btn-sm btn-outline-secondary rounded-pill px-4" @click="back">Back</button>
            </div>
        </div>
    </div>
</template>