<template>
    <ul class="liste">
        <li v-for="(fruit, index) in fruits" v-bind:key="index">{{fruit}} </li>
    </ul>
</template>

<script>

export default {
    name:'Liste',
    data: function(){
        return {
            fruits: ['orange', 'Papaye', 'Fraise']
        }
    }
}

</script>

<style scoped src="./Liste.css">



</style>
