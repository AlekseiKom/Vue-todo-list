<template>
  <div>
   <h2>Дела</h2>
   <router-link to="/" style="font-family:cursive">На главную страницу</router-link>
   <hr>
   <AddTodo
     @add-todo="addTodo"
   />
  <!--<select v-model="filter">
     <option value="all">Все дела</option>
     <option value="completed">Выполненое</option>
     <option value="not-completed">Не выполненое</option>
   </select>-->
   <hr>
   <Loader v-if="loading"/>
   <TodoList
   v-else-if='todos.length'
   v-bind:todos='todos'
   v-on:remove-todo="removeTodo"
    />
    <p v-else class="noTodos">Пока делать нечего !)</p>
  </div>
</template>

<script>
  import TodoList from '@/components/TodoList'
  import AddTodo from '@/components/AddTodo'
  import Loader from '@/components/Loader'
  import { setTimeout } from 'timers'

export default {
  name: 'app',
  data() {
    return {
      todos: [
       /*{id:1,title:'Купить хлеб', completed:false},
       {id:2,title:'Сходить на курсы', completed:false},
       {id:3,title:'Покормить кошек', completed:false},*/
      ],
       loading: true,
    }
  },
  mounted() {
     fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
        .then(response => response.json())
        .then(json => {
          setTimeout(() => {  
          this.todos = json
          this.loading = false
          }, 500)
        })
  },
  /*computed: {
     filteredTodos() {

       if ( this.filter === "all") {
         return this.todos
       }

       if ( this.filter === "completed") {
         return this.todos.filter(t => t.completed)
       }

       if ( this.filter === "not-completed") {
         return this.todos.filter(t => !t.completed)
       }
     }
  },*/
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  

  components: {
    TodoList, AddTodo, Loader
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  font-style: italic;
  font-size: 40px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  color: #2378da;
}
body{
  background: linear-gradient(#bcffbc,#74bcff);
  height: 1460px;
}
.noTodos {
  font-family: cursive;  
  font-size: 20px;
  color:#3f3f6b;
}

</style>
