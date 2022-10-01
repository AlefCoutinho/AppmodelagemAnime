<template>
  <v-app-bar app color="primary" dark>
    <div class="d-flex align-center">
        <!-- adiciona o logo vuetify -->
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />
        <!-- adiciona o nome (imagem) vuetify -->
        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>
      <!-- cria um espaço -->
      <v-spacer></v-spacer>
      <!-- adiciona os botões de navegação -->
      <v-btn to="/" text >
        <span class="mr-2">Início</span>
        <v-icon>mdi-home</v-icon>
      </v-btn>
      <v-btn to="/anime" text >
        <v-icon>mdi-plus</v-icon>
        <span class="mr-2">Anime</span>
      </v-btn>
      <v-btn to="/plataforma" text >
        <v-icon>mdi-plus</v-icon>
        <span class="mr-2">Plataforma</span>
      </v-btn>
      <v-btn to="/categoria" text >
        <v-icon>mdi-plus</v-icon>
        <span class="mr-2">Categoria</span>
      </v-btn>
      
      <v-btn to="/usuario" text >
        <v-icon>mdi-plus</v-icon>
        <span class="mr-2">Usuário</span>
      </v-btn>
      
      <v-btn to="/about" text >
        <span class="mr-2">Sobre</span>
        <v-icon>mdi-help</v-icon>
      </v-btn>
    </v-app-bar>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<style scoped>
  
</style>
