<template>
  <v-container>
    <v-row class="text-center ma-0">
      <v-col cols="12">
        <v-card class="v-theme--dark elevation-10">
          <v-responsive>
            <v-card-text class="titulo">BINGO</v-card-text>
          </v-responsive>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "TelaInicio",
  data: () => {},
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=EB+Garamond:ital,wght@0,400..800;1,400..800&family=Fredericka+the+Great&display=swap");

.titulo {
  font-family: "Fredericka the Great", serif;
  font-size: 15vmin;
  letter-spacing: 2.5rem;
  color: rgb(243, 240, 237);
  box-shadow: 3px 3px 10px rgb(28, 27, 27);
  padding: 10rem;
}
</style>
