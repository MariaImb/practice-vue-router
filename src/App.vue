<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
    <v-app>
        <v-app-bar :elevation="2">
            <v-app-bar-title>POKEAPI</v-app-bar-title>
            <RouterLink to="/"
                ><v-btn variant="text" class="btn-link">Home</v-btn></RouterLink
            >
            <RouterLink to="/pokemons"
                ><v-btn variant="text" class="btn-link"
                    >Pokemones</v-btn
                ></RouterLink
            >
            <RouterLink to="/favoritos"
                ><v-btn variant="text" class="btn-link"
                    >Favoritos</v-btn
                ></RouterLink
            >
        </v-app-bar>
        <RouterView />
    </v-app>
</template>

<style>
.btn-link {
    margin: 0px 20px !important;
}

.v-application__wrap {
    /* min-height: 0px !important; */
}
</style>
