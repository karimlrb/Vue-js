<template>
    <div class="container mt-5">

        <h1>{{titre}}</h1>
        <div class="btn btn-outline-primary me-2" v-on:click="component ='texte1'">Onglet 1</div>
        <div class="btn btn-outline-primary " v-on:click="component='texte2'">Onglet 2</div>

        <div class="onglets card mb-5">
            <component class="p-4" v-bind:is="component"></component>
        </div>
        <!-- <modale  v-bind:revel="revel"></modale> -->
        <modale v-bind:revele="revele" v-bind:toggleModale="toggleModale"></modale>
        <div v-on:click="toggleModale" class="btn btn-success">Ouvrir la modale</div><br>
        <img style="width:350px" class="mt-5" v-bind:src="urlImg" >
       
        
        
    
    </div>
</template>


<script>

    import axios from'axios'

    import Modale from './Modale.vue'
    import Texte1 from './Texte1'
    import Texte2 from './Texte2'

    export default{
        name:'Contenu',
        data:function(){
            return{
                urlImg: null,
                myArr: [
                    {titre: "Inception", date:2010},
                    {titre: "Avatar", date:2009},
                    {titre: "Seven", date:1995}
                ], 
                txt:"Les Affranchis", 
                titre:"Je suis le Titre",
                toggle1:true,
                toggle2:false,
                component: 'texte1',
                revele:false,
            }
        },
        methods: {
         toggleOng1: function(){
             this.toggle1 = true;
             this.toggle2 = false;
         },
         toggleOng2: function(){
             this.toggle1 = false;
             this.toggle2 = true;
         },
         toggleModale:function(){
             this.revele = !this.revele
         }
        },
        components: {
            'texte1':Texte1,
            'texte2':Texte2,
            'modale':Modale
        },
        mounted(){
            axios
            .get('https://api.thecatapi.com/v1/images/search')
            .then(reponse => {
               this.urlImg = reponse.data[0].url;
            }) 
        }
    }

</script>


<style>

    h1{
        margin-top: 100px!important;
    }

    .onglets{
        height: 200px;
    }

</style>