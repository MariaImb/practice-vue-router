<script setup>
import { ref } from "vue"
import axios from "axios"
import {RouterLink} from 'vue-router'

const pokemons = ref([]);

const getPokemones = async () => {
    try {
        const data = await axios.get("https://pokeapi.co/api/v2/pokemon");
        pokemons.value = data.data.results
    } catch (error) {
        console.error(error);
    }
};

getPokemones();
</script>

<template>
    <h1>Pokemones</h1>
    <ul >
        <li v-for="poke in pokemons" >
            <RouterLink :to="`/pokemons/${poke.name}`"> {{ poke.name }} </RouterLink>
      
        </li>
    </ul>
</template>
