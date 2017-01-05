<template>
  <div id="app">
    <div>
      <h1>Oracle Of Bacon</h1>

      <p>Vous pouvez rechercher la &quot;distance&quot; entre <b>Kevin Bacon</b> et un acteur de votre choix.
         Plus d'informations <a href="https://fr.wikipedia.org/wiki/Six_Degrees_of_Kevin_Bacon">ici.</a></p>
    </div>
    <div>
      <img src="./assets/kevin-bacon.png"/>
    </div>
    <actor-search></actor-search>
    <search-result id="result"></search-result>
  </div>
</template>

<script>
import ActorSearch from './components/ActorSearch';
import SearchResult from './components/SearchResult';

export default {
  name: 'app',
  components: {
    ActorSearch,
    SearchResult,
  },
};
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    /*text-align: center;*/
    /*color: #2c3e50;
    margin-top: 60px;*/
  }

  h1, p {
    text-align: center;
  }

  img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 300px;
  }

  #result {
    width: 400px;
    height: 400px;

    margin-left: auto;
    margin-right: auto;
  }

</style>
