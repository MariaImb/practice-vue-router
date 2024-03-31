<script setup>
import { ref } from "vue";
import { useRoute, useRouter } from "vue-router";
import { useGetData } from "../composables/getData";
import { useFavoritosStore } from "@/store/favoritos";

const route = useRoute();
const router = useRouter();

const { getData, data, loading } = useGetData();
const  useFavoritos = useFavoritosStore()
const {add, findPoke} = useFavoritos

const back = () => {
    router.push("/pokemons");
};

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);

</script>

<template>
    <v-progress-circular v-if="loading" indeterminate></v-progress-circular>
    <div v-if="data" class="poke-container">
        <img :src="data.sprites?.front_default" class="poke-img" />
        <h1>Poke name: {{ $route.params.name }}</h1>
        <v-btn :disabled="findPoke(data.name)" @click="add(data)" class="volver-btn">Agregar a Favorito 
        </v-btn>
 
    </div>

    <v-btn @click="back" class="volver-btn">Volver</v-btn>
</template>

<style scoped>
.volver-btn {
    width: 200px;
}

.poke-img {
    width: 200px;
    height: 200px;
}

.poke-container {
    margin-top: 50px;
}
</style>
