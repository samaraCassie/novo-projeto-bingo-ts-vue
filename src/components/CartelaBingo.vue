<template>
  <v-container class="v-theme--dark">
    <v-row class="text-center ma-0">
      <v-col cols="12" class="align-center justify-center ma-0">
        <div>
          <v-card
            class="my-5 v-theme--dark v-card--density-comfortable elevation-10 rounded"
          >
            <v-row w class="ma-1">
              <v-col>
                <v-card-title>{{ nomeJogador }}</v-card-title>
                <v-card-subtitle> Cartela 1 </v-card-subtitle>
              </v-col>
            </v-row>
            <v-row class="mr-10 ml-10 mb-10">
              <v-col cols="12" class="align-center">
                <v-table class="v-theme--dark">
                  <thead>
                    <tr>
                      <th
                        class="text-center"
                        v-for="coluna in colunas"
                        :key="coluna"
                      >
                        <v-col>{{ coluna }}</v-col>
                      </th>
                    </tr>
                  </thead>
                  <tbody class="">
                    <tr v-for="(item, index) in desserts" :key="index">
                      <td v-for="(numero, key) in item" :key="key">
                        <button
                          class="quadrado Coluna{{key}}"
                          @click="marcarBloco(index, key)"
                        >
                          <label>{{ numero }}</label>
                          <MarcadorBloco
                            :mostrar="blocosMarcados[index + key]"
                            @marcar-bloco="marcarBloco"
                          />
                        </button>
                      </td>
                    </tr>
                  </tbody>
                </v-table>
              </v-col>
            </v-row>
          </v-card>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import MarcadorBloco from "./MarcadorBloco.vue";

export default {
  name: "CartelaBingo",
  data() {
    return {
      colunas: ["B", "I", "N", "G", "O"],
      desserts: [
        { B: 0, I: 0, N: 0, G: 0, O: 0 },
        { B: 0, I: 0, N: 0, G: 0, O: 0 },
        { B: 0, I: 0, N: 0, G: 0, O: 0 },
        { B: 0, I: 0, N: 0, G: 0, O: 0 },
        { B: 0, I: 0, N: 0, G: 0, O: 0 },
      ],
      blocosMarcados: [
        { B: false, I: false, N: false, G: false, O: false },
        { B: false, I: false, N: false, G: false, O: false },
        { B: false, I: false, N: false, G: false, O: false },
        { B: false, I: false, N: false, G: false, O: false },
        { B: false, I: false, N: false, G: false, O: false },
      ],
    };
  },
  props: {
    nomeJogador: String,
  },
  mounted() {
    this.inicializarDesserts();
  },
  methods: {
    sorteio(min, max) {
      return Math.floor(Math.random() * (max - min + 1) + min);
    },
    numerosUnicos(quantidade, min, max) {
      const numerosUnicos = new Set();
      while (numerosUnicos.size < quantidade) {
        const numeroSorteado = this.sorteio(min, max);
        numerosUnicos.add(numeroSorteado);
      }
      return Array.from(numerosUnicos);
    },
    inicializarDesserts() {
      const quantidade = 1;
      let min = 1;
      let max = 15;

      for (let i = 0; i < this.desserts.length; i++) {
        for (let coluna in this.desserts[i]) {
          const listaNumerosSorteados = this.numerosUnicos(
            quantidade,
            min,
            max
          );

          this.desserts[i][coluna] = "";

          for (let j = 0; j < listaNumerosSorteados.length; j++) {
            if (this.desserts[i][coluna] !== "") {
              this.desserts[i][coluna] += " / " + listaNumerosSorteados[j];
            } else {
              this.desserts[i][coluna] = listaNumerosSorteados[j];
            }
          }

          min += 15;
          max += 15;
        }
      }
      console.log(this.desserts);
    },
    inicializarBlocosMarcados() {
      this.blocosMarcados = this.colunas.map((coluna) => {
        return this.colunas.reduce((acc, curr) => {
          acc[curr] = false; // Inicialize com valores booleanos padrão (false)
          console.log("coluna " + coluna);
          return acc;
        }, {});
      });
    },
    marcarBloco(index, key) {
      console.log("teste");
      /* this.blocosMarcados[key][index] = !this.blocosMarcados[key][index];*/
      console.log(`Bloco Marcado: `);
      console.log(`this.blocosMarcados` + this.blocosMarcados);
      console.log(`key` + key);
      console.log(`Index` + index);
      console.log(
        `this.blocosMarcados[index][key]` + this.blocosMarcados[index][key]
      );
    },

    /* desmarcarBloco(blocosMarcados, numero) {
      console.log("AEEEE");
      this.blocosMarcados.fill(blocosMarcados, numero, true); // Atualize o estado para redefinir a marcação
      console.log(`Bloco Dessmarcadoo: ` + blocosMarcados + numero);
    }, */
    ToggleMarcar(blocosMarcados, numero) {
      console.log("TESTE");
      if ((blocosMarcados, numero)) {
        this.marcarBloco(blocosMarcados, numero);
      } else {
        this.desmarcarBloco(blocosMarcados, numero);
      }
    },
    Teste() {
      console.log("Teste");
    },
  },
  components: {
    MarcadorBloco,
  },
};
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
