<template>
  <div class="container mt-5">
    <h1>{{ titre }}</h1>
    <div class="btn btn-outline-primary me-2" v-on:click="component = 'texte1'">
      Onglet 1
    </div>
    <div class="btn btn-outline-primary" v-on:click="component = 'texte2'">
      Onglet 2
    </div>

    <div class="onglets card mb-5">
      <component class="p-4" v-bind:is="component"></component>
    </div>
    <!-- <modale  v-bind:revel="revel"></modale> -->
    <modale v-bind:revele="revele" v-bind:toggleModale="toggleModale"></modale>
    <div v-on:click="toggleModale" class="btn btn-success">
      Ouvrir la modale
    </div>
    <br />
    <img class="mt-3" v-bind:src="urlImg" />

    <h2 class="mt-5">Notre Formulaire</h2>

    <form>
      <div class="form-group">
        <label for="prenom">Votre prénom</label>
        <input
          v-model="formData.prenom"
          type="text"
          id="prenom"
          class="form-control"
        />
      </div>

      <div class="form-group">
        <label for="txt">Votre Texte</label>
        <textarea
          v-model="formData.monTxt"
          id="txt"
          class="form-control"
        ></textarea>
      </div>

      <h3 class="mt-3">Select Box</h3>

      <select v-model="formData.select">
        <option v-bind:key="index" v-for="(pays, index) in formData.listePays">
          {{ pays }}
        </option>
      </select>

      <h3 class="mt-3">Checkboxs</h3>

      <div class="form-check">
        <input
          v-model="formData.checkFruits"
          value="fraise"
          id="fraise"
          type="checkbox"
          class="form-check-input"
        />
        <label for="fraise">Fraise</label>
      </div>

      <div class="form-check">
        <input
          v-model="formData.checkFruits"
          value="pomme"
          id="pomme"
          type="checkbox"
          class="form-check-input"
        />
        <label for="pomme">Pomme</label>
      </div>

      <div class="form-check">
        <input
          v-model="formData.checkFruits"
          value="cerise"
          id="cerise"
          type="checkbox"
          class="form-check-input"
        />
        <label for="cerise">Cerise</label>
      </div>

      <h2 class="mt-3">Résultats</h2>

      <div class="card p-3">
        <p>Pénom : {{ formData.prenom }}</p>
        <p style="white-space: pre">Texte : {{ formData.monTxt }}</p>

        <p>Résultats Checkboxs</p>

        <ul>
          <li v-bind:key="index" v-for="(fruit, index) in formData.checkFruits">
            {{ fruit }}
          </li>
        </ul>

        <p>Choix du Select : {{ formData.select }}</p>
      </div>
    </form>
  </div>
</template>


<script>
import axios from "axios";

import Modale from "./Modale.vue";
import Texte1 from "./Texte1";
import Texte2 from "./Texte2";

export default {
  name: "Contenu",
  data: function () {
    return {
      urlImg: null,
      myArr: [
        { titre: "Inception", date: 2010 },
        { titre: "Avatar", date: 2009 },
        { titre: "Seven", date: 1995 },
      ],
      txt: "Les Affranchis",
      titre: "Je suis le Titre",
      toggle1: true,
      toggle2: false,
      component: "texte1",
      revele: false,
      formData: {
        prenom: "",
        monTxt: "",
        checkFruits: [],
        select: "",
        listePays: ["Russie", "Japon", "Canada", "Mexique"],
      },
    };
  },
  methods: {
    toggleOng1: function () {
      this.toggle1 = true;
      this.toggle2 = false;
    },
    toggleOng2: function () {
      this.toggle1 = false;
      this.toggle2 = true;
    },
    toggleModale: function () {
      this.revele = !this.revele;
    },
  },
  components: {
    texte1: Texte1,
    texte2: Texte2,
    modale: Modale,
  },
  mounted() {
    axios.get("https://api.thecatapi.com/v1/images/search").then((reponse) => {
      this.urlImg = reponse.data[0].url;
    });
  },
};
</script>


<style>
body {
  height: 200vh;
}
h1 {
  margin-top: 100px !important;
}

.onglets {
  height: 200px;
}
img {
  width: 230px;
}
</style>