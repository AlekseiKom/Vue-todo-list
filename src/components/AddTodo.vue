<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit" class="addTodo">Новое дело</button>  
  </form>  
</template>

<script>
export default {
    data () {
        return {
         title: ""
        }
    },
    methods: {
        onSubmit() {
        if (this.title.trim()) {
            const newTodo = {
                id: Date.now(),
                title: this.title,
                completed: false
            }
            this.$emit("add-todo", newTodo)
            this.title = ''
        }
      }
    }
}
</script>

<style scoped>
  form {
      display:flex;
      justify-content:center;
  }
  input {
      padding-left: 15px; 
      font-style: italic;
      font-size: 20px;
      color:#465555;
      height:30px;
      width: 350px;
      border-radius: 10px;
      background:linear-gradient(#bddbdb,#a0e4eb);
      box-shadow: inset 2px 2px 5px rgba(154, 147, 140, 0.5), 1px 1px 5px rgba(255, 255, 255, 1);
  }
  .addTodo {
      margin-left: 7px;
      width: 150px;
      background:linear-gradient(#1a74db,#4ce03f);
      border-radius:10px;
      font-size: 17px;
      font-weight: bold;
      box-shadow: inset 2px 2px 5px rgba(154, 147, 140, 0.5), 1px 1px 5px rgba(255, 255, 255, 1);
  }
  .addTodo:hover {
      cursor:pointer;
      opacity: 0.8;
  }
</style>