<template>
    <div class="container mt-5">
        <p>
        {{txt}}
        </p>
        <liste v-bind:prenom="prenom"></liste>
    </div>
</template>


<script>

    import Liste from './Liste/Liste.vue'

    export default{
        name:'Contenu',
        data:function(){
            return{
                txt: 'Je suis le contenu',
                prenom: function(){
                    console.log("Hello from Parent");
                }
            }
        },
        components: {
        'liste':Liste
        },
    }

</script>


<style></style>