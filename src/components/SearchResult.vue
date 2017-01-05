<template>
  <div id="cytos" style="height:200px; border:solid"/></div>
</template>

<script>
  import cytoscape from 'cytoscape';

  export default {
    name: 'search-result',
    mounted: () => {
      /* eslint-disable */
//      console.log(document.getElementById('result'));
      console.log(`this : ${this}`);
      /* eslint-enable */

      cytoscape({
        /* eslint-disable */
        container: document.getElementById('result'),
        /* eslint-enable */
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
              shape: 'hexagon',
              'background-color': 'red',
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
  #cytos {
      height: 800;

      top: 0px;
      left: 0px;
      margin-left: auto;
      margin-right: auto;
  }
</style>
