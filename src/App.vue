<template>
  <v-app class="v-theme--dark roboto">
    <v-main>
      <TelaInicio />
      <BoxDadosRodada></BoxDadosRodada>
      <!--<HelloWorld /> -->
      <CartelaBingo />
    </v-main>
  </v-app>
</template>

<script setup>
import CartelaBingo from "./components/CartelaBingo.vue";
import TelaInicio from "./components/TelaInicio.vue";
import BoxDadosRodada from "./components/BoxDadosRodada.vue";
import axios from "axios";
import { ref } from "vue";

const jogadores = ref();

axios
  .get("jogadores")
  .then((response) => {
    console.log(response.data);
    jogadores.value = response.data;
    console.log();
  })
  .catch((error) => {
    console.log(error);
  });
</script>
