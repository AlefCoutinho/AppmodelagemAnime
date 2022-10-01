<template>
    <v-container>
        <v-row class="text-center">
            <v-col offset-lg="2" lg="8" md="12">
            <v-row>
            <v-col cols="12">
            <v-text-field label="Categoria" v-model="categoria.nome" @keypress.enter="salvarCategoria"></v-text-field>

            </v-col>
            </v-row>
            <v-row>
            <v-col cols="12" class="text-right">
                <v-btn class="primary" @click="salvarCategoria">Salvar</v-btn>
            </v-col>
            </v-row>
            </v-col>
            </v-row>
            <v-row class="text-center lighten-4 blue">
            <v-col offset-lg="2" lg="8" md="12">
            <v-simple-table>
                <thead>
                <tr>
                    <th class="text-left" style="width: 75%">Categoria</th>
                    <th class="text-left">Ação</th>
                </tr>
                </thead>
                <tbody>
                    <tr v-for="(categoria, indice) in listaCategoria"
                        :key="indice"
                        :class="categoria.feita ? 'lighten-4 orange' : ''"
                    >
                        <td class="text-left">{{ categoria.nome }}</td>
                        <td>
                            <v-btn class="orange  lighten-1 white--text" @click="alterarCategoria(categoria)">
                                <v-icon left>mdi-wrench </v-icon>
                                Alterar
                            </v-btn>
                            <v-btn class="red lighten-1 white--text" @click="removerCategoria(categoria.id)">
                                <v-icon dark left>mdi-cancel </v-icon>
                                Remover
                            </v-btn>

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
        name: "CategoriaForm",
        data: () => ({
            categoria: {
                id: 0,
                nome: ""
            },
            listaCategoria: [],
            indice: -1

        }),
        mounted(){
            this.getCategorias();
        },
        methods: {
            async getCategorias(){
                const req = await fetch('http://localhost:3000/categorias');
                const data = await req.json();
                this.listaCategoria = data;
                console.log(this.listaCategoria)

            },
            limpaCategoria() {
                this.categoria = {
                    id: 0,
                    nome: ""
                };
                this.indice = -1;
            },
            async salvarCategoria() {
                                
                if(this.indice < 0){
                    const objData = JSON.stringify(this.categoria);
                    const req = await fetch('http://localhost:3000/categorias',
                    {
                        method: "POST",
                        body: objData,
                        headers: { 
                            "Content-type": "application/json"
                        }
                    });
                    const data = await req.json();
                    console.log(data);

                }else{
                    
                    const objData = JSON.stringify(this.categoria);
                    this.alterarCategoria(this.categoria);
                    const req = await fetch('http://localhost:3000/categorias/'+ this.indice,
                    {   
                        method: "PUT",
                        body: objData,
                        headers: {
                            "Content-type": "application/json"
                        }
                    });
                    const data = await req.json();
                    this.listaCategoria = data;
                }

                this.getCategorias();
                this.limpaCategoria();
            },

            async alterarCategoria(categ){

                this.indice = categ.id;
                this.categoria = categ;


                
            },
            async removerCategoria(indice){
                const req = await fetch('http://localhost:3000/categorias/'+indice,
                {
                    method: "DELETE",
                    headers: { 
                        "Content-type": "application/json"
                    }
                });
                const data = await req.json();
                console.log(data);
                this.getCategorias();

            }
        }

    };
</script>

<style scoped>
    
</style>