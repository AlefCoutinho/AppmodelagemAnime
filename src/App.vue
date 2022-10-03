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
    <Footer />
  </v-app>

</template>

<script>
  import Navbar from "./components/Header.vue"
  import Footer from "./components/Footer.vue"
  export default {
    components:{
      Navbar,
      Footer
    },
    name: 'App',
    data: () => ({
    //
    }),
  };
</script>
