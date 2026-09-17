<script setup>
// import { ref } from 'vue';
// import axios from 'axios';
import { RouterLink } from 'vue-router';
import { useGetData } from '@/composables/getData.js';



const { data, getData } = useGetData();
getData("https://pokeapi.co/api/v2/pokemon");
</script>
<template>
    <div class="container d-flex flex-column align-items-center my-4">
        <h3 class="fw-bold text-dark mb-4">Pokemons</h3>

        <div class="w-100" style="max-width: 24rem;" v-if=data>
            <ul class="list-group list-group-flush bg-transparent gap-2">
                <li v-for="pokemon in data?.results" :key="pokemon.name"
                    class="list-group-item border-0 shadow-sm rounded-3 p-0 bg-body overflow-hidden">
                    <router-link :to="`/pokemons/${pokemon.name}`"
                        class="d-block p-3 text-decoration-none text-dark fw-medium text-capitalize text-center transition-all btn btn-outline-secondary rounded-3 w-100">
                        {{ pokemon.name }}
                    </router-link>
                </li>
            </ul>
            <div>
                <button :disabled="!data.next" class="btn btn-outline-primary mt-3" @click="getData(data?.next)">Cargar
                    más</button>
                <button :disabled="!data.previous" class="btn btn-outline-danger mt-3 ms-2"
                    @click="getData(data?.previous)">Cargar menos</button>
            </div>
        </div>
    </div>
</template>