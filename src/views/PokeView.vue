<script setup>
import axios from "axios";
import { ref } from "vue";
import { useRoute, useRouter } from "vue-router";
import { useGetData } from "../composables/getData";

const route = useRoute();
const router = useRouter();
const pokemon = ref({});

const { getData, data, loading, error } = useGetData();

const back = () => {
    router.push("/pokemons");
};

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);

// const getPokemon = async () => {
//     try {
//         const data = await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
//         pokemon.value = data.data
//         console.log(data.data)
//     } catch (error) {
//         console.error(error);
//     }
// };

// getPokemon();
</script>

<template>
    <v-progress-circular v-if="loading" indeterminate></v-progress-circular>
    <div v-if="data" class="poke-container">
        <img :src="data.sprites?.front_default" class="poke-img" />
        <h1>Poke name: {{ $route.params.name }}</h1>
    </div>

    <button @click="back" class="volver-btn">Volver</button>
</template>

<style scoped>
.volver-btn {
    width: 100px;
}

.poke-img {
    width: 200px;
    height: 200px;
}

.poke-container {
    margin-top: 50px;
}
</style>
