<template>
  <div style="visibility: hidden;" class="cytos box" ref="cytos"/></div>
</template>

<script>
  import cytoscape from 'cytoscape';

  // const elements = [
  //   {
  //     data: {
  //       id: 'a',
  //     },
  //   },
  //   {
  //     data: {
  //       id: 'b',
  //     },
  //   },
  //   {
  //     data: {
  //       id: 'c',
  //     },
  //   },
  //   {
  //     data: {
  //       id: 'd',
  //     },
  //   },
  //   {
  //     data: {
  //       id: 'e',
  //     },
  //   },
  //   {
  //     data: {
  //       id: 'ab',
  //       source: 'a',
  //       target: 'b',
  //     },
  //   },
  //   {
  //     data: {
  //       id: 'ac',
  //       source: 'a',
  //       target: 'c',
  //     },
  //   },
  // ];

  const elements2 = [
    {
      data: {
        id: 102720,
        type: 'Actor',
        value: 'McNally, Stephen (I)',
      },
      position: {
        x: 0,
        y: 0,
      },
    },
    {
      data: {
        id: 102721,
        type: 'Actor',
        value: 'McNally, Stephen (II)',
      },
    },
    {
      data: {
        id: 1102722,
        type: 'Actor',
        value: 'McNally, Stephen (III)',
      },
    },
    {
      data: {
        id: 2035857,
        type: 'Movie',
        value: 'Vendetta (1942)',
      },
      position: {
        x: 300,
        y: 500,
      },
    },
    {
      data: {
      //  id: 1027201,
        source: 102720,
        target: 2035857,
        value: 'PLAYED_IN',
      },
    },
];

const drawChart = (container, graphElements) => {
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
              if (node.data('value') === 'Bacon, Kevin (I)' || node.data('value') === 'Hitler, Adolf') {
                return '200px';
              }
              return '100px';
            },
            height: (node) => {
              if (node.data('value') === 'Bacon, Kevin (I)' || node.data('value') === 'Hitler, Adolf') {
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
    mounted() {
      cytoscape({
        container: this.$refs.cytos,
        layout: {
          name: 'preset',
        },
        elements: elements2,
        style: [
          {
            selector: 'node',
            style: {
              'background-color': '#37403F',
              label: 'data(value)',
            },
          },
          {
            selector: 'edge',
            style: {
              label: 'data(value)',
            },
          },
        ],
      });
    },
    watch: {
      actorName(newName) {
        if (newName) {
          this.$refs.cytos.style.visibility = 'visible';
          fetch('http://localhost:8080/api/bacon-to?actor=zadzad')
            .then(response => response.json())
            .then((bodyJson) => {
              console.log(JSON.stringify(bodyJson));
              // if (1 === 3) {
              drawChart(this.$refs.cytos, bodyJson);
              // }
            });
        } else {
          this.$refs.cytos.style.visibility = 'hidden';
        }

        // this.$refs.cytos.style.visibility = 'visible';
        // console.log('reload');
      },
    },
  };
</script>

<style scoped>
  .cytos {
      width: 1000px;
      height: 600px;
  }

</style>
