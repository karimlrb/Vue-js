<template>
    <div>
        <p>
        {{txt}}
        </p>
        <liste></liste>
    </div>
</template>


<script>

    import Liste from './Liste/Liste.vue'

    export default{
        name:'Contenu',
        data:function(){
            return{
                txt: 'Je suis le contenu'
            }
        },
        components: {
        'liste':Liste
        },
    }

</script>


<style></style>