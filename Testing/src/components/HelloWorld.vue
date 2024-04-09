

<template>

<div v-if="loading">
<div class="spinner-border" role="status" >
  <span class="visually-hidden">Loading...</span>
</div>
  <p>Carregando... Aguarde!!!</p>
</div>
    <div v-for="(dado, index) in dados" :key="index" v-if="!loading">
     <p class="title">Titulo: {{ dado.title }}</p>
     <p class="subtitle">Id: {{ dado.id }}</p>
     <p class="sub">{{ dado.completed }}</p>
    </div>

</template>


<script>

import axios from 'axios';

export default{
data() {
  return {
    dados: [],
    loading: true
  }
},

mounted() {

 setTimeout(() => {
  this.fetchData()
 }, 2000);
  
},

methods: {
  
    fetchData(){

      axios.get("https://jsonplaceholder.typicode.com/todos").then(Response=>{
        this.dados = Response.data;
        this.loading = false;
        console.log(this.dados)

      }).catch(error=>{
        console.log("DEU PAU")
      })
    }


},
}

</script>


<style scoped>
.read-the-docs {
  color: #888;
}

.title{
  background-color: #2EBDB3;
  border-radius: 2px;
  padding: 4px;
  box-shadow: 10px 10px 24px -12px rgba(0,0,0,0.58);
}
.subtitle{
  background-color: #7968AA;
}
.sub{

  background-color: #FCCF32;
}
.spinner-border{
    width: 120px;
    height:120px;
}
</style>
