<template>
  <div v-if="" class="cytos box" ref="cytos" style=""/></div>
</template>

<script>
  import cytoscape from 'cytoscape';

  const elements = [
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
  ];

  const drawChart = (container) => {
    cytoscape({
      container,
      layout: {
        name: 'circle',
      },
      elements,
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
  };

  export default {
    name: 'search-result',
    props: {
      actorName: String,
    },
    mounted() {
      cytoscape({
        container: this.$refs.cytos,
        layout: {
          name: 'circle',
        },
        elements,
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
    watch: {
      actorName(newName) {
        console.log(`newName: ${newName}`);
        drawChart(this.$refs.cytos);
      },
    },
  };
</script>

<style scoped>
  .cytos {
      width: 400px;
      height: 400px;
  }


</style>
