<template>
    <div id="cliente" @mouseenter="cor()">
        <h4>Nome:  {{cliente.nome}}</h4>
        <hr>
        <p>Email: {{cliente.email}}</p>
        <p v-show="showidade === true">Idade: {{cliente.idade}}</p>
        <button @click="mudarcor">MUDAR COR</button>
        <button @click="apagarevento">APAGAR</button>
        <h4>Id Especial: {{idEspecial}}</h4>
    </div>
</template>

<script>
export default {
    data(){
        return{
        }
    },

    props: {
        cliente: Object,
        showidade: Boolean
    },

    methods:{
        mudarcor: function(){
            alert("chamou um evento")
        }, 
        
        apagarevento: function(){
            alert("apagado")
            this.$emit("meDelete",{curso: "testatstetatatwt", empromocao: true});
        }
    },

    computed:{
            idEspecial: function(){
                return(this.cliente.email + this.cliente.nome + this.cliente.id).toUpperCase();
            }
        }
}
</script>

<style scoped>
 #cliente{
     border-radius: 2%;
     background-color: #ECE5E3;
     width: 200px;
     height: 150px;
     padding: 1%;
     margin-left: 2%;
     margin-top: 2%;

     display: inline-block;
 }

 #cliente-nome{
     color: maroon;
 }
</style>