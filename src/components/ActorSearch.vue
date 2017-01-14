<template>
  <div>
    <div class="form-container">
      <input placeHolder="Type Actor Name Here" class="actor-name" v-model="searchInput" @keypress.enter="search(searchInput)" @keypress="suggest(searchInput)"></input>
      <button class="search-button" @click="search(searchInput)">Search</button>
      <div v-show="searchInput" class="suggest" >
        <div v-for="suggest in suggests" class="suggest-item" @click="search(suggest)">{{suggest}}</div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'actor-search',
    props: {
      onSearch: Function,
    },
    data() {
      return {
        searchInput: undefined,
        suggests: undefined,
        // msg: 'Kevin Bacon',
      };
    },
    methods: {
      search(toSearch) {
        this.onSearch(toSearch);
        this.searchInput = '';
      },
      suggest(toSuggest) {
        fetch(`/api/suggest?q=${toSuggest}`)
        .then(response => response.json())
        .then((json) => {
          console.log('setting this.suggests');
          console.log(`toSuggest : ${toSuggest}`);
          this.suggests = json;
          console.log(`this.suggests ${JSON.stringify(this.suggests)}`);

          // this.searchInput = toSuggest;
        });
      },
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
    border:none;
    /*border:solid 2px #37403F;*/
    /*border-radius: 5px;*/
    text-align:center;
    width: 220px;
    height: 30px;
    font-size: 15px;
    display:inline-block;
    padding: 0px;
    /*opacity: 0.75;*/
    background-color:lightgray;
  }
  .search-button {
    border:none;
    color: #fbffc3;
    /*border-radius: 5px;*/
    font-size: 15px;
    position: absolute;
    top : 0;
    right: 0;
    bottom: 0;
    display:inline-block;
    background-color:#5A847E;
  }

  .suggest {
    /*border:solid 3px #37403F;*/
    border:none;
    position: absolute;
    width: 220px;
    /*border-radius: 5px;*/
    text-align: center;

    background-color: white;
    margin-top: 2px;
    /*box-shadow: 2px 2px 2px 1px grey;*/
    z-index: 100;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    /*display: none;*/
  }

  .suggest-item:hover {
    background-color: #bbcba4;
    cursor: pointer;
  }

</style>
