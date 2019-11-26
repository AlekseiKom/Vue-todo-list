<template>
<li>
  <span v-bind:class="{done: todo.completed}">
    <input type="checkbox" v-on:change="todo.completed=!todo.completed">
    <bold style="color:red">{{ index + 1}}</bold>
    {{todo.title | uppercase}}
  </span>
  <button class="rm" 
  v-on:click="$emit('remove-todo',todo.id)">&times;
  </button>
  
</li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        },
        index: Number
    },
    filters: {
      uppercase(value) {
          return value.toUpperCase()
      }  
    }
}
</script> 

<style scoped>
li {
    /*border: 1px solid #000;*/
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
    border-radius: 10px;
    box-shadow: inset 2px 2px 5px rgba(154, 147, 140, 0.5), 1px 1px 5px rgba(255, 255, 255, 1);
    font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    font-style:italic;
    font-weight: bold;
}
.rm {
    color:#cee4f6;
    background: linear-gradient(#ff1111,#f69b9b);
    border:none;
    border-radius: 5px;
}
.rm:hover {
     cursor:pointer;
     opacity: 0.7;
}
input {
    margin-right: 1rem;
}

.done {
   text-decoration: line-through;
}

</style>