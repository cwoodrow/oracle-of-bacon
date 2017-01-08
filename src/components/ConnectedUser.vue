<template>
  <!-- <div class="connected-user"> -->
    <img class="connected-user" src="../assets/avatar.jpg"></img>
  <!-- </div> -->
</template>

<script>
  export default {
    name: 'connected-user',
    data() {
      return {
        msg: 'Kevin Bacon',
      };
    },
  };
</script>

<style scoped>
  .connected-user {
    border-radius: 50%;
    max-width: 50px;
    max-height: 50px;
    border:solid 3px #37403F;
  }
</style>
