Skip to content
This repository
Search
Pull requests
Issues
Marketplace
Explore
 @AlexandraMaquet
 Sign out
 Watch 0
  Star 0  Fork 3 olivorel/testVue
forked from code-forefront/testVue
 Code  Pull requests 0  Projects 0  Wiki  Insights
Tree: 77b2c72f75 Find file Copy pathtestVue/src/components/_layout/Exercices/Exercice2/index.vue
77b2c72  8 days ago
@olivorel olivorel exercice 2 ok
2 contributors @olivorel @djodjonx
RawBlameHistory    
88 lines (85 sloc)  2.94 KB
<template>
  <div class="first-container">
    <div class="header">
      <div class="buttons">
        <div class="button" @click="$router.go(-1)">
          Précédent
        </div>
        <div class="button" @click="$router.push({name: 'exercice3'})">
          Suivant
        </div>
      </div>
      <div class="title">
        Ton deuxième défi, le composant dynamique.
      </div>
      <div class="content">
        <p>Le but de cet exercice est de mettre en place un composant dynamique qui changera au clique sur un nom d'une liste.</p>
        <p>A chaque clique sur un des noms, le composant devra changer d'état.</p>
        <p>Les composants à afficher se situent dans le dossier "./_subs/" </p>
        <p>Aucun style imposé</p>
      </div>
    </div>
    <div class="body">
      <div class="left">
        <ul class="themes">
          Thèmes:
          <li>Dynamique Components</li>
          <li>Event listener</li>
        </ul>
      </div>
      <div class="separator">
      </div>
      <div class="right">
        Liste des composants :
        <!-- ton code ici -->
        <div>
          <ul>
            <span @click="changeTheDisplayedComponent('composant1')">composants1</span>
            <span @click="changeTheDisplayedComponent2('composant2')">composants2</span>
            <span @click="changeTheDisplayedComponent3('composant3')">composants3</span>
  
            <li v-if="visible1">
              <component1></component1>
            </li>
            <li v-if="visible2">
              <component2></component2>
            </li>
            <li v-if="visible3">
              <component3></component3>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
  import Component1 from './_subs/Component1.vue'
  import Component2 from './_subs/Component2.vue'
  import Component3 from './_subs/Component3.vue'
  
  export default {
    data() {
      return {
        visible1: false,
        visible2: false,
        visible3: false
      }
    },
    methods: {
      changeTheDisplayedComponent: function() {
        this.visible1 = true;
        this.visible2 = false;
        this.visible3 = false
      },
      changeTheDisplayedComponent2: function() {
        this.visible1 = false;
        this.visible2 = true;
        this.visible3 = false
      },
      changeTheDisplayedComponent3: function() {
        this.visible1 = false;
        this.visible2 = false;
        this.visible3 = true
      }
    },
    components: {
      Component1,
      Component2,
      Component3
    }
  }
</script>

<style>
  .right span {
    cursor: pointer;
  }
</style>