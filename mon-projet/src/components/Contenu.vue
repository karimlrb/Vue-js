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
        <div v-on:click="toggleModale" class="btn btn-success">Ouvrir la modale</div>
       
        
        
    
    </div>
</template>


<script>
    import Modale from './Modale.vue'
    import Texte1 from './Texte1'
    import Texte2 from './Texte2'

    export default{
        name:'Contenu',
        data:function(){
            return{
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