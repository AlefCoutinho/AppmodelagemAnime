<template>
  <div class="geral-home">
  <v-carousel hide-delimiters>
    <v-carousel-item
      v-for="(item,i) in items"
      :key="i"
      :src="item.src"
    >
    <v-sheet
          :color="item"
          height="100%"
          tile
        >
          <v-row
            class="fill-height"
            align="center"
            justify="center"
          >
            <div class="text-h2">
              Slide {{ i + 1 }}
            </div>
          </v-row>
        </v-sheet></v-carousel-item>
  </v-carousel>
  <div class="titulo-home"><h3> site perfeito para Achar e compartilhar seu anime preferido</h3></div>
  <div class="titulo-corpo">Neste site você pode cadastrar e/ou procurar um anime, selecionando por plataforma e/ou anime, vendo em qual plataforma este anime está.<v-spacer></v-spacer>
  </div>
</div>
</template>

<script>
  export default {
    data () {
      return {
        items: [
          {
            src: 'https://external-preview.redd.it/ryM5Of3jMa7iHYyBMXFxyPhqnOofeip2S-Mgvf7p5R8.jpg?auto=webp&s=7ab34592345aca178e7906b5cfb61c5fc741e186',
          },
          {
            src: 'https://www.oficinadanet.com.br/imagens/post/17844/capa.jpg',
          },
          {
            src: 'https://mfiles.alphacoders.com/771/771677.jpg',
          },
          {
            src: 'https://i.pinimg.com/236x/1d/7e/31/1d7e3198ba00f72b7234ed82cc21a4e7.jpg',
          },
        ],
      }
    },
  }
</script>
<style>
  .v-main{
  padding: 56px 0px 60px!important;
}
.titulo-home{
  margin: 20px 20px 20px 20px;
  align-items: center;
  text-align: center;
  font-weight: bold;
  text-transform: uppercase;
}
.titulo-corpo{
  margin: 20px 20px 20px 20px;
  align-items: center;
  text-align: center;
}
</style>