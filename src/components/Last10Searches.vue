<template>
  <div class="last-10-searches">
    <!-- <input :placeHolder="msg" class="actor-name"></input>
    <button class="search-button">Search</button> -->
    <h3>Last 10 searches</h3>
    <ol>
      <li>Kevin Spacey</li>
    </ol>
  </div>
</template>

<script>
  export default {
    name: 'last-10-searches',
    data() {
      return {
    //    msg: 'Kevin Bacon',
      };
    },
  };
</script>

<style scoped>
  .last-10-searches {
      padding-right: 25px;
  }
</style>
