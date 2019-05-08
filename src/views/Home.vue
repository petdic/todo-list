<template>
  <div class="home">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todo_items="todo_list" v-on:delete-item-on-list="deleteTodo"/> 
    <!-- v-bind:[key]="value" will dynamically bind the attribute. When used for prop binding, 
    the prop must be properly declared in the child component -->

    <!-- Props are custom attributes you can register on a component. 
    When a value is passed to a prop attribute, it becomes a property on that component instance -->

    <!-- we can use v-bind to dynamically pass props -->
    <!-- in this example we are passing the array of objects todo_list -->
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from "@/components/HelloWorld.vue";
import Todos from '../components/Todos.vue';
import AddTodo from '../components/AddTodo.vue';
import axios from 'axios'

export default {
  name: "home",
  components: {
    Todos,
    AddTodo
  },
  data () {
    return {
      todo_list: []
    }
  },
  methods: {
    deleteTodo(id) {      
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => this.todo_list = this.todo_list.filter(item => item.id !== id))
      .catch(err => console.log(err));      
    },
    addTodo(newTodo){
      const {title, completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })  
      .then(res => this.todo_list= [...this.todo_list, res.data])
      .catch(err => console.log(err));          
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => this.todo_list = res.data)
    .catch(err => console.log(err));
  }
};
</script>
