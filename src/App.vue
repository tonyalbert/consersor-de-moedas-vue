<template>
  <div id="app">

    <h1 class="titulo">CONVERSOR DE MOEDAS</h1>

    <div class="linha">
      <Conversor moedaA="USD" moedaB="BRL"/>
      <Conversor class="abaixo" moedaA="BRL" moedaB="USD"/>
    </div>

    <div class="linha">
      <Conversor moedaA="EUR" moedaB="BRL"/>
      <Conversor class="abaixo" moedaA="BRL" moedaB="EUR"/>
    </div>

    <footer>
      <a href="https://www.linkedin.com/in/tonyalbert789/" target="blank">LinkedIn</a>
      <a href="https://github.com/tonyalbert" target="blank">GitHub</a>
    </footer>
  </div>

  
</template>

<script>
import Conversor from "./components/Conversor.vue"

export default {
  name: 'App',
  components: {
    Conversor
  }
}
</script>

<style>

*{
  margin: 0;
}

body{
  background-color: #00171f;
}

.titulo{
  color: white;
  font-size: 7vh;
}

#app {
  margin: auto;
  max-width: 750px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px; 
}

.linha{
  display: flex;
  justify-content: space-around;
  margin-top: 30px;
}

footer {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  background-color: #03212b;
  text-align: center;
  word-spacing: 20px;
  padding: 5px;
}

footer a {
  color: white;
  text-decoration: none;
  margin: 30px;
}

footer a:hover {
  color: #00a8e8; /* muda a cor do texto quando o cursor estiver sobre o link */
  text-decoration: double; /* adiciona uma linha debaixo do link quando o cursor estiver sobre ele */
}

@media screen and (max-width: 730px) {
  .linha{
    display: block;
    align-content: center;
  }

  .abaixo{
    margin-top: 30px;
    margin-bottom: 60px;
  }

  #app {
  max-width: 300px;
  }

  .titulo{
    font-size: 4vh;
  }

}

</style>
