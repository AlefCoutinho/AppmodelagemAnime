<template>
  <v-footer dark padless>
    <v-card class="flex green darken-4" flat tile>
      <v-card-title class="green darken-2">
        <strong class="subheading">Nos siga no GitHub!</strong>

        <v-spacer></v-spacer>

        <v-btn v-for="icon in icons" :key="icon" class="mx-4" dark icon>
          <v-icon size="24px">
            {{ icon }}
          </v-icon>
        </v-btn>
      </v-card-title>

      <v-card-text class="py-2 white--text text-center">
        {{ new Date().getFullYear() }} —
        <strong>ESDEV - Todos os Direitos e Esquerdos estão reservados!</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>
<script>
export default {
  name: "Footer",
  data: () => ({
    icons: [
      "mdi-github",
      "mdi-github",
      "mdi-github",
      "mdi-github",
      "mdi-github",
      "mdi-github",
    ],
  }),
};
</script>
