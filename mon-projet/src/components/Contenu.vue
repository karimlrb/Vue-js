<template>
    <div class="container mt-5">

        <h1>{{titre}}</h1>

        <liste v-bind:myArr="myArr"  :txt="txt">
             <p>Envoyez</p> 
             <template v-slot:info>
                 <h1>Le contenu du slot nommé</h1>
             </template>
        </liste>
    </div>
</template>


<script>

    import Liste from './Liste/Liste.vue'

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
            }
        },
        methods: {
         
         },
        components: {
        'liste':Liste
        },
    }

</script>


<style>

    h1{
        margin-top: 100px!important;
    }

</style>