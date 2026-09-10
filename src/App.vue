<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <nav class="navbar bg-transparent py-4">
    <div class="container d-flex flex-column align-items-center justify-content-center text-center gap-3">
      <router-link to="/pokemons"
        class="navbar-brand d-flex flex-column align-items-center text-decoration-none p-0 m-0">
        <img
          src="https://s.yimg.com/lo/mysterio/api/2918a337094e0ef14c61e3b4fd7d38cd46dbc7b8cd5cb67af1cd25a06285ffa2/lightyear_networkapi/resizefill_w976%3Bquality_80%3Bformat_webp/https%3A%2F%2Fs.yimg.com%2Fos%2Fcreatr-uploaded-images%2F2022-12%2Fa3a34890-7f03-11ed-a7e9-6563dc325d4d"
          alt="Messi de la suerte" width="80" height="80" class="rounded-circle shadow-sm object-fit-cover mb-2" />
        <span class="text-muted small fw-medium">Apretá a Messi de la suerte para ver los pokemones</span>
      </router-link>
      <router-link to="/about" class="btn btn-sm btn-outline-secondary rounded-pill px-4">About</router-link>
    </div>
  </nav>

  <div class="container text-center my-4">
    <RouterView />
  </div>
</template>