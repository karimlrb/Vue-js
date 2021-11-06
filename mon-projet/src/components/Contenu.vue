<template>
  <div class="container mt-5">
    <h1>Entrez des taches</h1>

    <form>
      <div class="form-group">
        <label for="action">Action</label>
        <input
          v-model="formData.tache"
          type="text"
          id="action"
          class="form-control"
        />

        <button v-on:click.prevent="creationItem" class="btn btn-primary my-4">
          Créer une tâche
        </button>
      </div>
    </form>

    <ul>
      <li v-bind:key="index" v-for="(tache, index) in tableauTaches">
        <item
          v-bind:id="index"
          v-bind:tache="tache"
          v-bind:suppression="suppression"
        ></item>
      </li>
    </ul>
  </div>
</template>


<script>
import Item from "./Item.vue";
export default {
  name: "Contenu",
  data() {
    return {
      formData: {
        tache: "",
      },
      tableauTaches: ["Javascript", "POO", "Typescript", "Vue", "Prestashop"],
    };
  },
  methods: {
    creationItem: function () {
      this.tableauTaches.push(this.formData.tache);
      this.formData.tache = "";
    },
    suppression: function (e) {
      //   console.log(e.target.parentNode.id);
      // On va à l'el e.target.parentNode.id et on enlève 1 el
      //   C a d qu'on supprime l'el cliqué
      this.tableauTaches.splice(e.target.parentNode.id, 1);
    },
  },
  components: {
    item: Item,
  },
};
</script>


<style>
h1 {
  margin-top: 100px !important;
}
ul {
  list-style-type: none;
  padding: 0 !important;
}
</style>