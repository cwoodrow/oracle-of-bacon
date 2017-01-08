<template>
  <div>
    <div class="form-container">
      <input :placeHolder="msg" class="actor-name"></input>
      <button class="search-button">Search</button>
      <div class="suggest">
        <div>Kevin Spacey</div>
        <div>Kevin Spacey</div>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'actor-search',
    data() {
      return {
        msg: 'Kevin Bacon',
      };
    },
  };
</script>

<style scoped>
  body {
    box-sizing: border-box;
  }

  .form-container {
    width: 300px;
    margin: 5px auto;
    position: relative;
    text-align: left;
  }
  .actor-name {
    border:solid 3px #37403F;
    border-radius: 5px;
    text-align:center;
    width: 220px;
    height: 30px;
    font-size: 15px;
    display:inline-block;
    opacity: 0.75;
    background-color:lightgray;
  }
  .search-button {
    border:solid 3px #37403F;
    border-radius: 5px;
    font-size: 15px;
    position: absolute;
    top : 0;
    right: 0;
    bottom: 0;
    display:inline-block;
    opacity: 0.75;
    background-color:lightgray;
  }

  .suggest {
    border:solid 3px #37403F;
    position: absolute;
    width: 220px;
    border-radius: 5px;
    text-align: center;

    background-color: white;
    margin-top: 2px;
    box-shadow: 2px 2px 2px 1px grey;
    z-index: 100;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    display: none;
  }

</style>
