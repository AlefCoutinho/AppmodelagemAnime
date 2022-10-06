<template>
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
  <div class="about">
    <h1>About</h1>
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
</style>