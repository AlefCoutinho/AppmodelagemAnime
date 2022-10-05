<template>
  <v-footer dark padless>
    <v-card class="flex green darken-4" flat tile>
      <v-card-title class="green darken-2">

          <strong class="">Nos siga no GitHub!</strong>  
          
          <!-- <v-spacer></v-spacer> -->

          <a v-for="(dev_p, i) in github" target="_blank" :key="i" :href="dev_p.link" class="mm" dark icon>
            <v-icon size="24px">
              mdi-github
            </v-icon>
            {{dev_p.nome}}    
          </a>


      </v-card-title>

      <v-card-text class="py-2 white--text text-center">
        Copyright ©  {{ new Date().getFullYear() }} —
        <strong>ESDEV - Todos os Direitos e Esquerdos estão reservados!</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>
<script>
export default {
  name: "Footer",
  data: () => ({
    github: [
      {
        nome:"Álef",
        link:"https://github.com/alefvieira"
    },
      {
        nome:"Eric",
        link:"https://github.com/ericdourado"
    },
      {
        nome:"Eduardo",
        link:"https://github.com/Lobistico"
    },
      {
        nome:"Paulo Coura",
        link:"https://github.com/PHCoura"
    },
      {
        nome:"Luiz Fernando",
        link:"https://github.com/LuizFernando96"
    },
      {
        nome:"Renato",
        link:"https://github.com/renatoplopes"
    }
    ],
  }),
};
</script>
<style>
  a.mm{
    text-decoration: none;
    color:white !important;
    padding: 20px;
  }
  a.mm:hover{
    text-decoration: none;
    color:#00000080 !important;
  }
  .v-card__title {
    justify-content: center;
  }
</style>