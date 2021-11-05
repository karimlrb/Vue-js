<template>
<div>
    <ul class="liste">
        <li v-for="(fruit, index) in fruits" v-bind:key="index">{{fruit}} </li>
    </ul>
    <p>{{ }}</p>
    
</div>
</template>

<script>

export default {
    name:'Liste',
    data: function(){
        return {
            fruits: ['orange', 'Papaye', 'Fraise']
        }
    },
    props: {
        prenom:{
            type:Function, 
            required:true
        }
    }
 
}

</script>

<style scoped src="./Liste.css">



</style>
