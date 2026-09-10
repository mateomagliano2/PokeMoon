<script setup>
import { ref } from 'vue';
import axios from 'axios';
import { RouterLink } from 'vue-router';

const pokemons = ref([]);
const getData = async () => {
    try {
        const { data } = await axios.get('https://pokeapi.co/api/v2/pokemon');
        pokemons.value = data.results;
        console.log(data);
    } catch (error) {
        console.log(error);
    }
}
getData();
</script>
<template>
    <div class="container d-flex flex-column align-items-center my-4">
        <h3 class="fw-bold text-dark mb-4">Pokemons</h3>

        <div class="w-100" style="max-width: 24rem;">
            <ul class="list-group list-group-flush bg-transparent gap-2">
                <li v-for="pokemon in pokemons" :key="pokemon.name"
                    class="list-group-item border-0 shadow-sm rounded-3 p-0 bg-body overflow-hidden">
                    <router-link :to="`/pokemons/${pokemon.name}`"
                        class="d-block p-3 text-decoration-none text-dark fw-medium text-capitalize text-center transition-all btn btn-outline-secondary rounded-3 w-100">
                        {{ pokemon.name }}
                    </router-link>
                </li>
            </ul>
        </div>
    </div>
</template>