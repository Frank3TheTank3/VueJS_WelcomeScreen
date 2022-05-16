<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo_op.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
      <ul class="listElement">
        <li class="center">Coffee</li>
        <li class="center">Tea</li>
        <li class="center">Milk</li>
      </ul>
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}



.listElement li {
  list-style-type: none;
  background-color: rgb(54, 51, 120);
  font-size: 30px;
  color: chocolate;
  margin: 50px;
  line-height: 150px;
}


</style>
