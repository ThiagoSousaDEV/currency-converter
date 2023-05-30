<template>
  <div id="app">
    <h1>Conversor de Moedas</h1>
    <div class="linha">
    <Conversor moedaA="USD" moedaB="BRL" />
    </div>
  </div> 
</template>

<script>
import Conversor from "./components/Conversor.vue";
export default {
  name: "App",
  components: {
    Conversor,
  },
};
</script>

<style>
body {
  background-color: #038eb1;
}

#app {
  margin: auto;
  max-height: 900px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  margin-top: 60px;
}
.linha {
  margin-top: 40px;
  display: flex;
  justify-content: space-around;
}
</style>
