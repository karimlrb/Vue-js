<template>
<div>
    <ul class="liste mt-5">
        <li v-for="(film, index) in myArr" v-bind:key="index">
          <div class="card">
              <div class="card-body">
                  Titre :  {{film.titre}} <br>  Date : {{film.date}} 
              </div>
          </div>
        </li>
    </ul>
    <p>{{txt}}</p>
   <div class="btn btn-danger mt-2" v-on:click="deleteFilm">Supprimer le film</div>
   <div class="btn btn-danger mt-2 ms-5" v-on:click="deleteText">Supprimer le Texte</div>
   <div class="btn btn-primary mt-2 ms-5" v-on:click="changeTitre">Changer le Titre</div>
    
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
    methods: {
        deleteFilm: function(){
            // pop supprime le dernier élément d'un tableau
            this.myArr.pop()
        }, 
        deleteText: function(){
            this.txt=""
        },
        changeTitre: function(){
            this.$emit('changeTitre', "Mon nouveau Titre")
        }
    },
    props:['myArr', 'txt'], 
   
 
}

</script>

<style scoped src="./Liste.css">



</style>
