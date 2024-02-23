<template>
  <v-container class="pa-10 d-flex justify-center align-center">
    <v-row class="justify-center">
      <v-col cols="6">
        <v-row class="pb-10">
          <v-col>
            <v-card class="v-theme--dark elevation-10 rounded pa-10 pt-2">
              <v-row>
                <v-col>
                  <v-card-title class="text-sm-center">Teste</v-card-title>
                </v-col>
              </v-row>
              <v-row v-for="jogador in jogadores" :key="jogador.id">
                <v-col>{{ jogador.nome }}</v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
        <v-card class="v-theme--dark elevation-10 rounded">
          <v-form v-model="valid" class="ma-15">
            <v-row>
              <v-col>
                <v-card-tittle>Informações da Rodada:</v-card-tittle>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12">
                <v-text-field
                  v-model="QntJogadores"
                  :rules="QntJogadoresRules"
                  :counter="10"
                  label="Quantos Jogadores"
                  required
                  hide-details
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12">
                <v-text-field
                  v-model="nomeJogador"
                  :rules="nomeRules"
                  label="Nome do Jogador"
                  hide-details
                  required
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12">
                <v-text-field
                  v-model="QntCartelas"
                  :rules="QntCartelasRules"
                  label="Quantas Cartelas"
                  hide-details
                  required
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="3" class="mr-n5">
                <v-btn type="submit"> Jogar </v-btn>
              </v-col>
              <v-col cols="3">
                <v-btn @click="handleReset"> Limpar </v-btn>
              </v-col>
            </v-row>
          </v-form>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
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

const valid = ref(false);
const nomeJogador = ref("");
const nomeRules = [
  (value) => {
    if (value) return true;
    return "Informe o Nome.";
  },
  (value) => {
    if (value?.length <= 10) return true;
    return "Nome deve ter menos de 10 caracteres.";
  },
];
const QntCartelas = ref(0);
const QntCartelasRules = [
  (value) => {
    if (value) return true;
    return "Informe a quantidade de cartelas.";
  },
  (value) => {
    if (value <= 5) return true;
    return "Limitado à 4 cartelas.";
  },
];
const QntJogadores = ref(0);
const QntJogadoresRules = [
  (value) => {
    if (value) return true;
    return "Informe a quantidade de jogadores.";
  },
  (value) => {
    if (value <= 5) return true;
    return "No minimo 2 jogaros e no maximo 4.";
  },
];
</script>

<style></style>
