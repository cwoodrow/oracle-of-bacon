<template>
  <div style="visibility: hidden;" class="cytos box" ref="cytos"/></div>
</template>

<script>
  import cytoscape from 'cytoscape';

  const drawChart = (container, graphElements, newName) => {
    cytoscape({
      container,
      layout: {
        name: 'circle',
      },
      elements: graphElements,
      style: cytoscape.stylesheet()
        .selector('node')
          .style({
            'background-color': (node) => {
              if (node.data('type') === 'Movie') {
                return '#617d57';
              } else if (node.data('type') === 'Actor') {
                return '#30514c';
              }
              return 'black';
            },
            width: (node) => {
              if (node.data('value') === 'Bacon, Kevin (I)' || node.data('value') === newName) {
                return '200px';
              }
              return '100px';
            },
            height: (node) => {
              if (node.data('value') === 'Bacon, Kevin (I)' || node.data('value') === newName) {
                return '200px';
              }
              return '100px';
            },
            'text-valign': 'center',
            'text-halign': 'center',
            'text-outline-color': (node) => {
              if (node.data('type') === 'Movie') {
                return '#617d57';
              } else if (node.data('type') === 'Actor') {
                return '#30514c';
              }
              return 'black';
            },
            'text-outline-width': 10,
            color: 'white',
            'text-wrap': 'wrap',
            // 'font-size': '200px',
            label: 'data(value)',
          })
        .selector('edge')
          .style({
            'curve-style': 'bezier',
            'control-point-step-size': 40,
            'target-arrow-shape': 'triangle',

          }),
      // style: [
      //   {
      //     selector: 'node',
      //     style: {
      //       'background-color': '#37403F',
      //       label: 'data(value)',
      //     },
      //   },
      //   {
      //     selector: 'edge',
      //     style: {
      //   //    label: 'data(value)',
      //     },
      //   },
      // ],
    });
  };

  export default {
    name: 'search-result',
    props: {
      actorName: String,
    },
    watch: {
      actorName(newName) {
        if (newName) {
          this.$refs.cytos.style.visibility = 'visible';
          fetch(`/api/bacon-to?actor=${newName}`)
            .then(response => response.json())
            .then((bodyJson) => {
              console.log(JSON.stringify(bodyJson));
              drawChart(this.$refs.cytos, bodyJson, newName);
            });
        } else {
          this.$refs.cytos.style.visibility = 'hidden';
        }
      },
    },
  };
</script>

<style scoped>
  .cytos {
      width: 1000px;
      height: 600px;
      /*background-color: #bbcba4;*/
  }

</style>
