<template>
  <v-app-bar app color="green darken-2">
    <div class="d-flex align-center">
      <!-- adiciona o logo vuetify -->
      <!-- <v-img
                alt="LOLIZINHA"
                class="shrink mr-12"
                contain
                src="../../src/assets/EGIRL.png"
                transition="scale-transition"
                width="40"
            /> -->
      LOLIZINHA
      <!-- adiciona o nome (imagem) vuetify -->
      <!-- <v-img
        alt="Vuetify Name"
        class="shrink mt-1 hidden-sm-and-down"
        contain
        min-width="100"
        src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
        width="100"
      /> -->
    </div>
    <!-- cria um espaço -->
    <v-spacer></v-spacer>
    <div class="text-center" center>
      <v-menu offset-x>
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="green darken-4" center dark v-bind="attrs" v-on="on">
            Menu
          </v-btn>
        </template>
        <v-list>
          <v-list-item>
            <v-list-item-title>
              <v-btn to="/" text>
                <span class="mr-2">Início</span>
              </v-btn>
            </v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>
              <v-btn to="/anime" text>
                <span class="mr-2">Anime</span>
              </v-btn>
            </v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>
              <v-btn to="/plataforma" text>
                <span class="mr-2">Plataforma</span>
              </v-btn>
            </v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>
              <v-btn to="/categoria" text>
                <span class="mr-2">Categoria</span>
              </v-btn>
            </v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
      |
      <v-btn to="/about" depressed color="green darken-4"> Sobre </v-btn>
    </div>
  </v-app-bar>
</template>

<script>
export default {
  name: "Navbar",
  data: () => ({}),
};
</script>

<style scoped></style>
