<template>
  <div id="app">
   <h1>Мой список дел</h1>
   <hr>
   <router-view/>
  </div>
</template>

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

</style>
