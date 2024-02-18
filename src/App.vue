<template>
  <v-app class="v-theme--dark roboto">
    <v-main>
      <TelaInicio />
      <BoxDadosRodada :nomeJogador="nomeJogador" v-if="post"></BoxDadosRodada>/>
      <!-- <HelloWorld /> -->
      <CartelaBingo />
    </v-main>
  </v-app>
</template>

<script>
/* import HelloWorld from "./components/HelloWorld.vue"; */
import CartelaBingo from "./components/CartelaBingo.vue";
import TelaInicio from "./components/TelaInicio.vue";
import BoxDadosRodada from "./components/BoxDadosRodada.vue";

export default {
  name: "App",

  components: {
    /*HelloWorld, */
    CartelaBingo,
    TelaInicio,
    BoxDadosRodada,
  },

  data() {},
};
</script>
