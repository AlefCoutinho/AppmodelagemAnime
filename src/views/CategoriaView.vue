<template>
  <div class="categoria">
    <h1>Categoria Page</h1>
    <CategoriaForm/>
  </div>
</template>

<script>
  import CategoriaForm from "../components/CategoriaForm.vue"

  export default {
    name: "CategoriaView",
    components:{
      CategoriaForm,
    }
  }
</script>
