<template>
  <v-container>
    <div class="text-center" center>
      <v-dialog v-model="dialog" width="500">
        <template v-slot:activator="{ on, attrs }">
          <v-btn-toggle v-model="toggle_exclusive" mandatory center>
            <v-btn
              center
              rounded
              elevation="2"
              color="yellow darken-2"
              dark
              large
              class="text-center black--text"
              v-bind="attrs"
              v-on="on"
            >
              Novo Anime
            </v-btn>
            <v-spacer></v-spacer>
            <v-spacer></v-spacer>
            <v-btn
              center
              rounded
              elevation="2"
              color="yellow darken-2"
              dark
              large
              class="text-center black--text"
              @click="hidden = !hidden"
            >
              {{ hidden ? "Cadastrados" : "Ocultar" }}
            </v-btn>
          </v-btn-toggle>
        </template>

        <v-card>
          <v-card-title
            class="justify-center text-h5 black--text yellow darken-2 rounded"
            rounded
          >
            Informações do Anime
          </v-card-title>

          <v-card-text class="green lighten-5">
            <v-spacer>.</v-spacer>
            <v-row class="text-center green lighten-5" rounded>
              <v-col offset-lg="2" lg="8" md="12">
                <v-form v-model="valid">
                  <v-row>
                    <v-col cols="12">
                      <v-text-field label="Nome" v-model="anime.nome"></v-text-field>
                      <v-text-field
                        label="Diretor"
                        v-model="anime.diretor"
                      ></v-text-field>
                      <v-text-field
                        label="Estudio"
                        v-model="anime.estudio"
                      ></v-text-field>
                      <v-select
                        v-model="anime.qtdtemporadas"
                        :items="itemsQtdTemp"
                        label="Quantidade de temporadas"
                      >
                      </v-select>
                      <v-textarea
                        v-model="anime.sinopse"
                        label="Sinopse"
                        value="Digite aqui a sinopse"
                      >
                      </v-textarea>

                      <v-select
                        v-model="addCategoria"
                        :items="categorias"
                        label="Categorias"
                      >
                      </v-select>
                      <v-btn text @click="setCategoria">
                        <v-icon>mdi-plus</v-icon>
                        <span class="mr-2">Categoria</span>
                      </v-btn>
                      <ul>
                        <li
                          v-for="(cat, indice) in anime.categorias"
                          :key="indice"
                          class="text-left"
                        >
                          {{ cat }}
                          <v-btn-toggle v-model="toggle_none" rounded>
                            <v-btn
                              class="red darken-1 white--text small"
                              @click="removeCategoria(indice)"
                            >
                              <v-icon dark center>mdi-cancel</v-icon></v-btn
                            >
                          </v-btn-toggle>
                        </li>

                        <p></p>
                      </ul>

                      <v-select
                        v-model="addPlataforma"
                        :items="plataformas"
                        label="Plataformas"
                      >
                      </v-select>
                      <v-btn text @click="setPlataforma">
                        <v-icon>mdi-plus</v-icon>
                        <span class="mr-2">Plataforma</span>
                      </v-btn>

                      <ul>
                        <li v-for="(plat, indice) in anime.plataformas" :key="indice">
                          {{ plat }}
                          <v-btn-toggle v-model="toggle_exclusive">
                            <v-btn
                              class="red darken-4 white--text"
                              @click="removePlataforma(indice)"
                            >
                              <v-icon dark center>mdi-cancel </v-icon></v-btn
                            >
                          </v-btn-toggle>
                        </li>
                      </ul>

                      <v-text-field
                        type="date"
                        label="Data de lançamento"
                        v-model="anime.dtlancamento"
                      ></v-text-field>
                      <v-text-field
                        type="number"
                        label="Quantidade de episódios"
                        v-model="anime.qtdEp"
                      ></v-text-field>
                      <v-select
                        v-model="anime.statusDoAnime"
                        :items="statusDoAnime"
                        label="Status Do Anime"
                      >
                      </v-select>
                      <v-text-field
                        type="number"
                        label="Nota"
                        v-model="anime.nota"
                      ></v-text-field>
                    </v-col>
                  </v-row>
                </v-form>
              </v-col>
            </v-row>
          </v-card-text>

          <v-divider></v-divider>

          <v-card-actions color="blue darken-4">
            <v-spacer></v-spacer>
            <v-btn
              block
              rounded
              elevation="2"
              color="blue darken-4"
              class="white--text"
              @click="salvarAnime"
            >
              Salvar
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
    <v-space>.</v-space>

    <v-row class="text-center" v-show="!hidden">
      <v-col offset-lg="2" lg="8" md="12">
        <v-simple-table rounded-pill>
          <thead>
            <tr>
              <th v-for="(anime, indice) in listaAnime" :key="indice">
                <v-card :loading="loading" class="mx-auto" max-width="350">
                  <template slot="progress">
                    <v-progress-linear
                      color="deep-purple"
                      height="10"
                      indeterminate
                    ></v-progress-linear>
                  </template>

                  <v-img
                    height="250"
                    src="https://i.pinimg.com/736x/58/53/83/585383da22c40c31cea4d9181df39ff1.jpg"
                  ></v-img>

                  <v-card-title>{{ anime.nome }}</v-card-title>

                  <v-card-text>
                    <v-row align="center" class="mx-0"> </v-row>

                    <div class="my-4 text-subtitle-1">
                      {{ anime.estudio }} {{ anime.statusDoAnime }}
                      {{ anime.dtlancamento }} |
                    </div>
                    <div>
                      {{ anime.sinopse }}
                    </div>
                  </v-card-text>
                  <v-divider class="mx-4"></v-divider>
                  <v-card-text>
                    <v-row align="center" class="mx-0"> </v-row>

                    <div class="my-4 text-subtitle-1">
                      {{ anime.diretor }}
                    </div>
                    <div>
                      Disponível na {{ anime.plataformas }} <br />
                      Com {{ anime.qtdtemporadas }} temporadas e {{ anime.qtdEp }} de
                      episódios.<br />Categorias: {{ anime.categorias }} <br />Avaliação:
                    </div>
                  </v-card-text>

                  <v-divider class="mx-4"></v-divider>

                  <v-card-actions>
                    <v-btn-toggle
                      v-model="toggle_multiple"
                      center
                      align="center"
                      justify="center"
                    >
                      <v-btn
                        class="yellow darken white--text center"
                        @click="alterarAnime(anime)"
                      >
                        <v-icon center>mdi-wrench</v-icon>
                      </v-btn>

                      <v-btn
                        class="yellow darken-2 center"
                        @click="removerAnime(anime.id)"
                        center
                      >
                        <v-icon center>mdi-cancel</v-icon>
                      </v-btn>
                    </v-btn-toggle>
                  </v-card-actions>
                </v-card>
              </th>
            </tr>
          </thead>
          <tbody>
            <tr></tr>
          </tbody>
        </v-simple-table>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "animeForm",
  data: () => ({
    hidden: true,
    dialog: false,
    valid: true,
    anime: {
      nome: "",
      diretor: "",
      estudio: "",
      qtdtemporadas: "",
      sinopse: "",
      categorias: [],
      plataformas: [],
      dtlancamento: "",
      qtdEp: "",
      statusDoAnime: "",
      nota: "",
    },
    errors: "",
    addCategoria: "",
    categorias: [],
    addPlataforma: "",
    plataformas: [],
    itemsQtdTemp: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20],
    statusDoAnime: ["Finalizado", "Em lançamento", "Em produção"],
    listaAnime: [],
    indice: -1,
  }),
  mounted() {
    this.getAnime();
    this.getCategorias();
    this.getPlataformas();
  },
  methods: {
    setCategoria() {
      if (!this.anime.categorias.includes(this.addCategoria) && this.addCategoria != "") {
        this.anime.categorias.push(this.addCategoria);
        this.addCategoria = "";
      } else {
        this.errors = "Não deve repetir a mesma categoria";
      }
    },
    removeCategoria(indice) {
      this.anime.categorias.splice(indice, 1);
    },
    setPlataforma() {
      if (
        !this.anime.plataformas.includes(this.addPlataforma) &&
        this.addPlataforma != ""
      ) {
        this.anime.plataformas.push(this.addPlataforma);
        this.addPlataforma = "";
      } else {
        this.errors = "Não deve repetir a mesma plataforma";
      }
    },
    removePlataforma(indice) {
      this.anime.plataformas.splice(indice, 1);
    },
    async getCategorias() {
      const req = await fetch("http://localhost:3000/categorias");
      const data = await req.json();
      data.map((data) => {
        this.categorias.push(data.nome);
      });
    },
    async getPlataformas() {
      const req = await fetch("http://localhost:3000/plataforma");
      const data = await req.json();
      data.map((data) => {
        this.plataformas.push(data.plataforma);
      });
    },
    async getAnime() {
      const req = await fetch("http://localhost:3000/anime");
      const data = await req.json();
      this.listaAnime = data;
    },
    limpaAnime() {
      this.anime = {
        id: 0,
        anime: "",
        email: "",
        senha: "",
      };
      this.indice = -1;
    },
    async salvarAnime() {
      if (this.indice < 0) {
        const objData = JSON.stringify(this.anime);
        const req = await fetch("http://localhost:3000/anime", {
          method: "POST",
          body: objData,
          headers: {
            "Content-type": "application/json",
          },
        });
        const data = await req.json();
        console.log(data);
      } else {
        const objData = JSON.stringify(this.anime);
        this.alterarAnime(this.anime);
        const req = await fetch("http://localhost:3000/anime/" + this.indice, {
          method: "PUT",
          body: objData,
          headers: {
            "Content-type": "application/json",
          },
        });
        const data = await req.json();
        this.listaAnime = data;
      }

      this.getAnime();
      this.limpaAnime();
      this.dialog = false;
    },

    async alterarAnime(anime) {
      this.indice = anime.id;
      this.anime = anime;
      this.dialog = true;
    },
    async removerAnime(indice) {
      const req = await fetch("http://localhost:3000/anime/" + indice, {
        method: "DELETE",
        headers: {
          "Content-type": "application/json",
        },
      });
      const data = await req.json();
      console.log(data);
      this.getAnime();
    },
  },
};
</script>

<style scoped></style>
