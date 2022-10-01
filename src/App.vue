<template>
  <!-- cria a tela de aplicação vuetify -->
  <v-app>
  <!-- cria a barra de aplicação vuetify -->
    <v-app-bar
      app
      color="primary"
      dark
    >
      <Navbar/>
    </v-app-bar>
    <!-- visão principal onde serão renderizadas as rotas -->
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
  import Navbar from "./components/Header.vue"

  export default {
    components:{
      Navbar,
    },
    name: 'App',
    data: () => ({
    //
    }),
  };
</script>
  