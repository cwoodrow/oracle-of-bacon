<template>
  <div class="form-container">
    <input :placeHolder="msg" class="actor-name"></input>
    <button class="search-button">Search</button>
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
    /*outline: 1px solid red;*/
    /*width: 300px;*/
    width: 300px;
    margin: 5px auto;
    position: relative;
    text-align: left;
  }
  .actor-name {
    border:solid 2px black;
    border-radius:5px;
    text-align:center;
    width: 220px;
    height: 30px;
    font-size: 15px;
    display:inline-block;
  }
  .search-button {
    border:solid 2px black;
    border-radius:5px;
    background-color: white;
    display:inline-block;
    font-size: 15px;
    position: absolute;
    top : 0;
    right: 0;
    bottom: 0;
    /*box-shadow:0 0 6px;*/
  }

</style>
