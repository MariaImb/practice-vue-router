<script setup>
import axios from "axios"
import { ref } from "vue"
import {useRoute, useRouter} from "vue-router"

const route = useRoute()
const router = useRouter()
const pokemon = ref({});

const back = () => {
    router.push('/pokemons')
}

const getPokemon = async () => {
    try {
        const data = await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
        pokemon.value = data.data
        console.log(data.data)
    } catch (error) {
        console.error(error);
    }
};

getPokemon();

</script>

<template>
    <h1>Poke name: {{ $route.params.name }}</h1>
    <img :src="pokemon.sprites.front_default"/>
    <button @click="back" class="volver-btn">Volver</button>
</template>

<style scoped>

.volver-btn {
    width: 100px;
}
</style>
