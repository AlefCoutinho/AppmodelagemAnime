<template>
    <v-container>
        <div class="text-center" center>
            <v-dialog v-model="dialog" width="500">
                <!-- adicionando os botões -->
                <template v-slot:activator="{ on, attrs }">
                    <v-btn-toggle mandatory center>
                        <v-btn
                            @click="limpaPlataforma"
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
                            Nova Plataforma
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
                        Cadastro
                    </v-card-title>
                    <v-card-text class="green lighten-5">
                        <v-spacer>.</v-spacer>
                        <v-row class="text-center green lighten-5" rounded>
                            <v-col offset-lg="2" lg="8" md="12">
                                <v-form v-model="valid">
                                    <v-row>
                                        <v-col cols="12">
                                            <v-text-field
                                                label="Plataforma"
                                                v-model="plataforma.plataforma"
                                            ></v-text-field>
                                            <v-select
                                                v-model="plataforma.tipoServico"
                                                :items="items"
                                                label="Tipo de Serviço"
                                            >
                                            </v-select>
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
                            @click="salvarPlataforma"
                        >
                            Salvar
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-dialog>
        </div>

        <v-row v-show="!hidden">
            <v-col offset-lg="2" lg="8" md="12">
                <div>
                    <v-text-field
                        label="Pesquisa..."
                        v-model="search"
                        @keypress.enter="searchPlataforma"
                    ></v-text-field>
                </div>
            </v-col>
        </v-row>

        <v-row class="text-center" v-show="!hidden">
            <v-col offset-lg="2" lg="8" md="12">
                <v-simple-table>
                    <thead>
                        <tr class="yellow darken-2 rounded" style="text-align:center" center>
                            <th class="text-left" style="width: 60%">
                                Plataforma
                            </th>
                            <th class="text-left">Tipo Serviço</th>
                            <th class="text-left">Ação</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr
                            v-for="(plataforma, indice) in listaPlataforma"
                            :key="indice"
                            :class="plataforma.feita ? 'lighten-4 orange' : ''"
                        >
                            <td class="text-left">
                                {{ plataforma.plataforma }}
                            </td>
                            <td class="text-left">
                                {{ plataforma.tipoServico }}
                            </td>
                            <td>
                                <v-btn-toggle
                                    center
                                    align="right"
                                    justify="right"
                                >
                                    <v-btn
                                        class="yellow darken white--text right"
                                        @click="alterarPlataforma(plataforma)"
                                    >
                                        <v-icon center>mdi-wrench</v-icon>
                                    </v-btn>

                                    <v-btn
                                        class="yellow darken-2 right"
                                        @click="removerPlataforma(plataforma.id)"
                                        center
                                    >
                                        <v-icon center>mdi-cancel</v-icon>
                                    </v-btn>
                                </v-btn-toggle>
                            </td>
                        </tr>
                    </tbody>
                </v-simple-table>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    name: "PlataformaForm",
    data: () => ({
        plataforma: {},
        listaPlataforma: [],
        indice: -1,
        items: ["Pago", "Grátis"],
        search: "",
        hidden: true,
        dialog: false,
        valid: true,
    }),
    mounted() {
        this.getPlataforma();
    },
    methods: {
        // MÉTODO GET
        async getPlataforma() {
            const req = await fetch("http://localhost:3000/plataforma");
            const data = await req.json();
            this.listaPlataforma = data;
        },
        // MÉTODO SEARCH (PESQUISA)
        async searchPlataforma() {
            const req = await fetch(
                "http://localhost:3000/plataforma?q=" + this.search
            );
            const data = await req.json();
            this.listaPlataforma = data;
        },
        // LIMPA OS CAMPOS
        limpaPlataforma() {
            this.plataforma = {
                id: 0,
                plataforma: "",
                tipoServico: "",
            };
            this.indice = -1;
        },
        // MÉTODO QUE VAI SALVAR E ATUALIZAR
        async salvarPlataforma() {
            if (this.indice < 0) {
                const objData = JSON.stringify(this.plataforma);
                const req = await fetch("http://localhost:3000/plataforma", {
                    method: "POST",
                    body: objData,
                    headers: {
                        "Content-type": "application/json",
                    },
                });
                const data = await req.json();
                console.log(data);
            } else {
                const objData = JSON.stringify(this.plataforma);
                this.alterarPlataforma(this.plataforma);
                const req = await fetch(
                    "http://localhost:3000/plataforma/" + this.indice,
                    {
                        method: "PUT",
                        body: objData,
                        headers: {
                            "Content-type": "application/json",
                        },
                    }
                );
                const data = await req.json();
                this.listaPlataforma = data;
            }

            this.getPlataforma();
            this.limpaPlataforma();
            this.dialog = false;
            this.limpaPlataforma();
        },
        // MÉTODO QUE VAI ALTERAR I INDICE PARA A EDIÇÃO DO VALOR
        async alterarPlataforma(plat) {
            this.indice = plat.id;
            this.plataforma = plat;
            this.dialog = true;
        },
        // MÉTODO QUE VAI REMOVER O OBJETO
        async removerPlataforma(indice) {
            const req = await fetch(
                "http://localhost:3000/plataforma/" + indice,
                {
                    method: "DELETE",
                    headers: {
                        "Content-type": "application/json",
                    },
                }
            );
            const data = await req.json();
            console.log(data);
            this.getPlataforma();
        },
    },
};
</script>

<style scoped></style>
