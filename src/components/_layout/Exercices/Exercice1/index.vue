<template>
  <div class="first-container">
    <div class="header">
      <div class="buttons">
        <div class="button" @click="$router.go(-1)">
          Précédent
        </div>
        <div class="button" @click="$router.push({name: 'exercice2'})">
          Suivant
        </div>
      </div>
      <div class="title">
        Ton premier défi, la TODO list.
      </div>
      <div class="content">
        <p>Si tu es familier de cet exercice, cela ne devrait pas poser de problème.</p>
        <p>Sinon l'exercice consiste à créer une liste, qui s'implémentera avec les valeurs que tu rentreras dans un input</p>
        <p>(bonus: créer un bouton pour supprimer un élément)</p>
      </div>
    </div>
    <div class="body">
      <div class="left">
        <ul class="themes">
          Thèmes:
          <li>List rendering</li>
          <li>Data Binging</li>
          <li>Event listener</li>
        </ul>
      </div>
      <div class="separator">
      </div>
      <div class="container">
        <div class="right">
          <!-- ton code ici -->
          <h1>TODO LIST</h1>
          <div>
            <label>Entrer une nouvelle tâche :</label> <br>
            <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Blabla">
            <div class="wrap-list">
              <ol class="list">
                <li v-for="todo in todos">
                  <span>{{ todo.text }}</span>
                  <button @click="remove(todo)">X</button>
                  <!-- <button v-on:click="delete(index)">x</button> -->
                </li>
              </ol>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        todos: [{
          text: 'ma première chose à faire'
        }, {
          text: 'ma deuxième chose à faire'
        }],
        newTodo: ''
      }
    },
    methods: {
      addTodo: function() {
        let text = this.newTodo
        if (text) {
          this.todos.push({
            text: text
          })
          this.newTodo = ''
        }
      },
      remove: function (todo) {
       this.todos.splice(this.todos.indexOf(todo), 1)
       }
      /*  delete:(index) {
         this.todos.splice(index, 1);
       } */
    }
  }
</script>

<style scoped>
  h1 {
    color: rgb(108, 128, 243);
    text-decoration: underline;
  }
  
  label {
    padding-bottom: 15px;
  }
  
  input {
    padding: 10px;
    border: 1px solid #2B49E9;
  }
  
  .list {
    padding-left: 0;
  }
  
  .list li {
    margin-top: 15px;
    border: 5px double #2B49E9;
    padding: 10px;
    color: rgb(58, 57, 57);
  }
</style>