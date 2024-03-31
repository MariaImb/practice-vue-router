<script setup>
import { useFavoritosStore } from "@/store/favoritos";
import { storeToRefs } from "pinia";
import { RouterLink } from "vue-router";
const useFavoritos = useFavoritosStore();

const { favoritos } = storeToRefs(useFavoritos);
const {remove} = useFavoritos
</script>

<template>
    <div class="favoritos-container">
        <h1>Favoritos</h1>
        <p v-if="favoritos.length === 0">Sin favoritos</p>
        <v-card class="list-card" v-else>
            <v-list class="text-center list-item" v-for="poke in favoritos">{{ poke.name }}
                <RouterLink :to="`/pokemons/${poke.name}`">Mas informacion</RouterLink>
                <v-btn @click="remove(poke.id)">Eliminar</v-btn></v-list>
        </v-card>

    </div>
</template>

<style>
.favoritos-container {
    margin-top: 70px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.list-card {
    width: 400px;
}

.list-item{
    border: grey 2px solid !important;
 
}
</style>
