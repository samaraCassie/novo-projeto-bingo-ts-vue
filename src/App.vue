<template>
  <v-app class="v-theme--dark roboto">
    <v-main>
      <TelaInicio />
      <BoxDadosRodada></BoxDadosRodada>
      <CartelaBingo></CartelaBingo>
    </v-main>
  </v-app>
</template>

<script setup>
import CartelaBingo from "./components/CartelaBingo.vue";
import TelaInicio from "./components/TelaInicio.vue";
import BoxDadosRodada from "./components/BoxDadosRodada.vue";
</script>
