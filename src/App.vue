<template>
  <div id="app">
    <div class="container">

    
    <h1 class="h1">What will you do?</h1>
    <AddItem 
    v-on:add-item="addItem"
    />
   <TodoList 
   v-bind:doings="doings"
   v-on:remove-item="removeItem"
   />
   </div>
    <!-- /.container -->
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddItem from "@/components/AddItem";

export default {
  name: "App",
   data() {
     return {
       doings: [
        {id: 1, title: 'Walking to the park', completed: false },
        {id: 2, title: 'To buy a military helicopter for son', completed: false },
        {id: 3, title: 'To wash a car', completed: false },
        {id: 4, title: 'Go to the cinema', completed: false }
      ]
    }
  },
  methods: {
    removeItem(id) {
      this.doings = this.doings.filter(i => i.id !== id);
    },
    addItem(item) {
      this.doings.push(item);
    }
  },
  components: {
    TodoList, AddItem
  },
 
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Mukta&display=swap');
#app {
  font-family: "Mukta", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  margin: 0 auto;
  padding: 0 10px;
  max-width: 700px;
}
button, input {
  cursor: pointer;
  outline: none;
}
ul {
  list-style: none;
}
</style>
