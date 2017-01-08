<template>
  <div id="app">
    <div>
      <div class="box">
        <h1>Oracle Of Bacon</h1>
      </div>
      <div class="box">
        <p>Vous pouvez rechercher la &quot;distance&quot; entre <b>Kevin Bacon</b> et un acteur de votre choix.
           Plus d'informations <a href="https://fr.wikipedia.org/wiki/Six_Degrees_of_Kevin_Bacon">ici.</a></p>
      </div>
    </div>
    <actor-search id="actor-search"></actor-search>
    <search-result id="result"></search-result>
    <last-10-searches id="last-10-searches" class="box"></last-10-searches>
    <connected-user id="connected-user"></connected-user>
  </div>
</template>

<script>
import ActorSearch from './components/ActorSearch';
import SearchResult from './components/SearchResult';
import Last10Searches from './components/Last10Searches';
import ConnectedUser from './components/ConnectedUser';

export default {
  name: 'app',
  components: {
    ActorSearch,
    SearchResult,
    Last10Searches,
    ConnectedUser,
  },
};
</script>

<style>
  h1, h3, p, ol {
    text-align: center;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    color: #37403F;
  }

  .box {
    border-radius: 10px;
    padding: 0px 5px 0px 5px;
    margin: 5px;
    opacity: 0.75;
    background-color:lightgray;
    border: solid;
    width: -webkit-fit-content;
    height: -webkit-fit-content;
    width: -moz-fit-content;
    height: -moz-fit-content;
    border:solid 3px #37403F;
    margin-left: auto;
    margin-right: auto;
  }

  html {
    background: url(./assets/kevin-bacon-background.png) no-repeat center center fixed;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
  }

  #last-10-searches {
    position: absolute;
    top: 210px;
    right: 50px;
  }

  #connected-user {
    position: absolute;
    top: 20px;
    right: 20px;
  }

  *:focus {
    outline: none;
  }

</style>
