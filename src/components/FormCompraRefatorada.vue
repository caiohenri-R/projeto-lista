
<template>
    <div class="container">
        <h1>Lista de Compras - {{ titulo }}</h1>
        <hr />
        <p><input type="text" v-model="produto" placeholder="Nome do Produto" class="form-control"></p>
        <p><input type="text" v-model="quantidade" placeholder="Quantidade do Produto" class="form-control"></p>
    <div v-if="isInvalido" class="alert alert-danger" role="alert">
        Nome do produto e quantidade devem ser preenchido!
    </div>
        <button type="submit" v-on:click.prevent="incluirProduto" class="btn btn-primary">Incluir</button>
        <hr/>      
    </div>
</template>

<script>
export default{
    props:{
        titulo:String
    }, 
   data(){
    return {
            produto: '',
            quantidade:'',
            isInvalido:false,
        
        }
     },
     methods:{
         incluirProduto(){
            console.log(this.produto , this.quantidade);
            if(this.produto ==='' || this.quantidade ===''){
                this.isInvalido = true;
                return;
            }
            this.isInvalido = false;

               this.$emit('novo-produto',{
               produto:this.produto,
               quantidade:this.quantidade 
            });

            this.produto = '';
            this.quantidade = '';
            
         },

     }
}
</script>
