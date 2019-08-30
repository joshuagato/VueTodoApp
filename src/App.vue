<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- {{ todos[1].title }} -->

    <!-- Get the todos which is an array of objects, into this Todos element -->
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todosProp="todosArray" v-on:delete-todo="deleteTodo" />
    <!-- <Bind v-bind:bindTitle="title" /> -->

  </div>
</template>

<script>
import Todos from './components/Todos.vue';
import Header from './components/layouts/Header.vue';
import AddTodo from './components/AddTodo.vue';
// import Bind from './components/layouts/Bind.vue';
// import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'app',
  components: {
    // HelloWorld
    Todos,
    Header,
    AddTodo,
    // Bind
  },
  data() {
    return {
      todosArray: [
        {
         id: 1,
         title: "Todo One",
         done: false 
        },

        {
         id: 2,
         title: "Todo Two",
         done: false 
        },

        {
         id: 3,
         title: "Todo Three",
         done: false 
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todosArray = this.todosArray.filter(eachTodoIteration => eachTodoIteration.id !== id);
    },
    addTodo(newTodo) {
      this.todosArray = [...this.todosArray, newTodo];
    }
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
