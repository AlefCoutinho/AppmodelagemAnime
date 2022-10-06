<template>
  <!-- cria a tela de aplicação vuetify -->
  <v-app >
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
    <Footer>
    </Footer>
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
<style>
  /* BARRA DE ROLAGEM */
  body::-webkit-scrollbar {
    width: 8px; /* width of the entire scrollbar */
  }

  body::-webkit-scrollbar-track {
    background: rgb(255, 255, 255);        /* color of the tracking area */
  }

  body::-webkit-scrollbar-thumb{
    background-color: #cf9e25;    /* color of the scroll thumb */
    border-radius: 0 20px 0 20px;       /* roundness of the scroll thumb */
    /*border: 3px solid #ffeb3b;  /*creates padding around scroll thumb*/
    border: 1px solid #fde402;  /*creates padding around scroll thumb*/
  }
  body::-webkit-scrollbar-thumb:hover {
    background-color: #fde402;    /* color of the scroll thumb */
    border-radius: 0 20px 0 20px;       /* roundness of the scroll thumb */
    /* border: 3px solid orange;  creates padding around scroll thumb */
  }
</style>