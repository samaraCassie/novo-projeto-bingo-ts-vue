<template>
  <span
    class="marcador"
    v-if="mostrar"
    @click="toggleMostrar"
    :style="{ display: mostrar ? 'none' : 'block' }"
    onclick="Teste"
  >
    {{ numero }}>X</span
  >
</template>

<script>
export default {
  name: "MarcadorBloco",
  props: {
    mostrar: Boolean,
    numeroBloco: Number,
  },
  emits: ["marcar-bloco", "resetar-marcacao"],
  methods: {
    toggleMostrar() {
      this.marcado = !this.marcado; // Alternar o estado do marcador ao clicar
      if (this.marcado) {
        this.marcarBloco();
      } else {
        this.resetarMarcacao();
      }
      console.log("teste");
    },
    marcarBloco() {
      this.emit("marcar-bloco", this.numeroBloco); // Emitir evento com número do bloco
    },
    resetarMarcacao() {
      this.emit("resetar-marcacao", this.numeroBloco);
    },
    Teste() {
      console.log("teste");
    },
  },
};
</script>

<style>
.marcador {
  position: absolute;
  z-index: 2;
  font-size: 55px;
  color: rgb(255, 0, 0);
  display: none;
}
</style>
