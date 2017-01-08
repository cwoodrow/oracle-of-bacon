<template>
  <div class="cytos box" ref="cytos" style=""/></div>
</template>

<script>
  import cytoscape from 'cytoscape';

  export default {
    name: 'search-result',
    mounted() {
      cytoscape({
        container: this.$refs.cytos,
        layout: {
          name: 'circle',
        },
        elements: [
          {
            data: {
              id: 'a',
            },
          },
          {
            data: {
              id: 'b',
            },
          },
          {
            data: {
              id: 'c',
            },
          },
          {
            data: {
              id: 'd',
            },
          },
          {
            data: {
              id: 'e',
            },
          },
          {
            data: {
              id: 'ab',
              source: 'a',
              target: 'b',
            },
          },
          {
            data: {
              id: 'ac',
              source: 'a',
              target: 'c',
            },
          },
        ],
        style: [
          {
            selector: 'node',
            style: {
              'background-color': '#37403F',
              label: 'data(id)',
            },
          },
          {
            selector: 'edge',
            style: {
              label: 'data(id)',
            },
          },
        ],
      });
    },
  };
</script>

<style scoped>
  .cytos {
      width: 400px;
      height: 400px;
  }


</style>
