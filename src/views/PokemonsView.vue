<script setup>
import { ref } from "vue";
import { RouterLink } from "vue-router";
import { useGetData } from "../composables/getData";

const { getData, data, loading, error } = useGetData();

getData("https://pokeapi.co/api/v2/pokemon");
</script>

<template>
    <div class="pokemons-container">
        <h1>Pokemones</h1>
        <v-alert v-if="error" :text=error type="error" class="error-container"></v-alert>
        <v-progress-circular v-if="loading" indeterminate></v-progress-circular>
        <div v-if="data">
            <ul>
                <li v-for="poke in data.results">
                    <RouterLink :to="`/pokemons/${poke.name}`">
                        {{ poke.name }}
                    </RouterLink>
                </li>
            </ul>
        </div>
    </div>
</template>

<style>
.pokemons-container {
    margin-top: 70px;
    margin-left: 30px;
}

.error-container {
    width: 300px;
    margin: 20px;
}
</style>
