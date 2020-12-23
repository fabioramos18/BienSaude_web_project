<template>
  <div id="app">
    <h3>Registar:</h3>
    <input type="text" placeholder="nome" v-model="nomeField"> <br>
    <small id="nomeError" v-show="deuerro">Insira um Nome valido</small> <br>
    <input type="email" placeholder="email" v-model="emailField"> <br>
    <input type="number" placeholder="idade" v-model="idadeField"> <br>
    <button @click="registaruser">Registar</button>
    <hr>
    
    <div v-for="(cliente,index) in orderClientes" :key="cliente.id">
      <h4>{{index + 1}}</h4>
        <cliente :cliente="cliente" @meDelete="deletecliente($event)" />
    </div>    
  </div>
</template>

<script>
import cliente from './components/cliente'
//import produto from './components/produto'
import _ from 'lodash';


export default {

  data(){
        return{
          deuerro: false,
        nomeField:"",
        emailField: "",
        idadeField: 0,

        clientes:[
          {
            id: 1,
            nome: "Fabio Ramos",
            email: "teste1@gmail.com", 
             idade: "99"
          },
          {
            id: 2,
            nome: "Pedro alves",
            email: "palvels@gmail.com", 
            idade: "25"
          },
        ]
        }
  },

  components: { cliente, 
  //produto
  },
  
  methods: {
     registaruser: function(){
       if(this.nomeField == "" || this.nomeField == " "||  this.nomeField.length < 3){
         this.deuerro = true;
       }else{
        this.clientes.push({nome: this.nomeField, email: this.emailField, idade: this.idadeField, id: Date.now()}),
        this.nomeField = "",
        this.emailField= "",
        this.idadeField= 0,
        this.deuerro = false;
       }
     },

     deletecliente: function($event){
       console.log("recebeu um evento");
       console.log($event)
     }
  },

  
     computed: {
       orderClientes: function() {
         return _.orderBy(this.clientes,['nome'], ['asc']);
       }
     }

}
</script>

<style>
#nomeError{
  color: red;
}
</style>
