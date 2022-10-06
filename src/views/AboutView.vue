<template>
  <v-container>
    <!-- <strong class="">Projeto</strong> -->

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
        <h3 class="rounded inline-block">
          <a :href="dev_p.link" target="_blank">
            <v-icon size="24px"> mdi-github </v-icon> {{ dev_p.nome }} 
          </a>
        </h3>
        {{ dev_p.funcao }}
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
.mm a{
  text-decoration: none;
  color: #031f03 !important;
  padding: 20px;
}
.mm a:hover {
  text-decoration: none ;
  color: #00000080 !important;
}
.v-card__title {
  justify-content: center;
}

li {
  list-style: none;
  padding: 5px;
}

h3 {
  background: #FFFDE7;
}
</style>