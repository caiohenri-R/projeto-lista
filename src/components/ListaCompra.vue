
<template>
    <div class="container">
        <h1>Lista de Compras</h1>
        <hr />
        <p><input type="text" v-model="produto" placeholder="Nome do Produto" class="form-control"></p>
        <p><input type="text" v-model="quantidade" placeholder="Quantidade do Produto" class="form-control"></p>
        <button type="submit" v-on:click.prevent="incluirProduto" class="btn btn-primary">Incluir</button>
        <hr/>
        <div class="list-group">
            <div class="list-group-item" v-for="(item, index) in lista" v-bind:key="index">
                <span><strong>{{item.produto}}</strong></span>
                <p>{{item.quantidade}}</p>
                <div>
                    <a href="#">Excluir</a>   
                </div>
            </div>              
       </div>
    </div>
</template>

<script>
export default{
   data(){
    return {
            produto: '',
            quantidade:'',
            lista: []
        
        }
     },
     methods:{
         incluirProduto(){
            console.log(this.produto , this.quantidade);
            this.lista.push({
                produto:this.produto,
                quantidade:this.quantidade 
            });
            this.produto = '';
            this.quantidade = '';
            
         }
     }
}
</script>
