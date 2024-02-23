<template>
  <v-container class="v-theme--dark">
    <v-row class="text-center ma-0">
      <v-col cols="12" class="align-center justify-center ma-0">
        <h2>Cartela de Bingo</h2>
        <div v-for="(jogador, index) in jogadores" :key="index">
          <p>{{ jogador.nome }} : {{ jogador.cartelasId }}</p>
          <div v-for="(cartelaId, index) in jogador.cartelasId" :key="index">
            <div v-for="(cartela, index) in cartelas" :key="index">
              <div v-if="cartela.id == cartelaId">
                <v-card
                  class="my-5 v-theme--dark v-card--density-comfortable elevation-10 rounded"
                >
                  <v-row>
                    <v-col>
                      <v-row>
                        <v-col>
                          <v-card-title
                            >{{ jogador.nome }} {{ cartela.id }}</v-card-title
                          >
                        </v-col>
                      </v-row>
                      <v-row class="mr-10 ml-10 mb-10">
                        <v-col cols="12" class="align-center">
                          <v-table class="v-theme--dark">
                            <thead>
                              <tr>
                                <th
                                  class="text-center"
                                  v-for="coluna in cartela.colunas"
                                  :key="coluna"
                                >
                                  <v-col>{{ coluna }}</v-col>
                                </th>
                              </tr>
                            </thead>
                            <tbody>
                              <tr
                                v-for="(item, index) in cartela.desserts"
                                :key="index"
                              >
                                <td v-for="(numero, key) in item" :key="key">
                                  <label>{{ numero }}</label>
                                </td>
                              </tr>
                            </tbody>
                          </v-table>
                        </v-col>
                      </v-row>
                    </v-col>
                  </v-row>
                </v-card>
              </div>
            </div>
          </div>
        </div>
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

const cartelas = ref();

axios
  .get("cartelas")
  .then((response) => {
    console.log(response.data);
    cartelas.value = response.data;
    console.log();
  })
  .catch((error) => {
    console.log(error);
  });
</script>

<style>
.quadrado {
  width: 100%;
  height: 100%;

  border: 1px solid rgb(156, 156, 156);

  display: flex;
  justify-content: center;
  align-items: center;

  font-size: 35px;
  font-weight: 600;

  cursor: pointer;
}

.secBotoes {
  display: flex;
  justify-content: center;
  align-items: center;

  margin-top: 20px;
}

.botoes {
  background-color: #000;
  color: #fff;
  cursor: pointer;
  padding: 10px;
}

.botoes:first-child {
  margin-right: 10px;
}

.ColunaB {
  background-color: rgb(255, 164, 164);
}

.ColunaI {
  background-color: rgb(172, 255, 177);
}

.ColunaN {
  background-color: rgb(248, 255, 180);
}

.ColunaG {
  background-color: rgb(209, 208, 255);
}

.ColunaO {
  background-color: rgb(255, 212, 177);
}
</style>
