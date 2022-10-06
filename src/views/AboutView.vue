<template>
  <v-container>
    <strong class="">Projeto</strong>

    <ul>
      <li 
        v-for="(dev_p, i) in github"
        target="_blank"
        :key="i"
        :href="dev_p.link"
        class="mm"
        dark
        icon
      >
        
        <h3 > <v-icon size="24px"> mdi-github </v-icon> {{ dev_p.nome }}</h3>
        {{dev_p.funcao}}
      </li>
    </ul>
  </v-container>
</template>
<script>
export default {
  name: "Footer",
  data: () => ({
    github: [
      {
        nome: "Álef",
        link: "https://github.com/alefvieira",
        funcao: "Desenvolvedor FullStack e Coordenador de Projetos",
      },
      {
        nome: "Eric",
        link: "https://github.com/ericdourado",
        funcao: "Desenvolver FullStack",
      },
      {
        nome: "Eduardo",
        link: "https://github.com/Lobistico",
        funcao: "Desenvolvedor Front End / UX",
      },
      {
        nome: "Paulo Coura",
        link: "https://github.com/PHCoura",
        funcao: "Analista de Requistos / UX",
      },
      {
        nome: "Luiz Fernando",
        link: "https://github.com/LuizFernando96",
        funcao: "Analista de Requistos",
      },
      {
        nome: "Renato",
        link: "https://github.com/renatoplopes",
        funcao: "Desenvolvedor Front End",
      },
    ],
  }),
};
</script>
<style>
a.mm {
  text-decoration: none;
  color: white !important;
  padding: 20px;
}
a.mm:hover {
  text-decoration: none;
  color: #00000080 !important;
}
.v-card__title {
  justify-content: center;
}


li{
  list-style:none;
}
</style>