<template>
    <Plotly
        :id="plotId"
        :data="plotData"
        :layout="layout"
        :display-mode-bar="false"
    ></Plotly>
</template>

<script>
  import { Plotly } from "vue-plotly";
  export default {
    name: "bar_chart",
    components: {
      Plotly,
    },
    props: {
      plotId: { required: true, type: String },
      aggregatedData: { required: true, type: Array },
    },
    data: function() {
      return {
        plotData: [
          {
            x: this.aggregatedData.map(row => row.key),
            y: this.aggregatedData.map(row => row.value),
            type: "bar",
            marker: {
               color: "#5dc275", //colore barra
              opacity: 0.9,
              line: {
                color: "black",
                width: 1,
              },
            },
          },
        ],
        layout: {
          title: this.plotId,
          xaxis: {
            tickfont: {
              size: 10,
              color: "#000000",
            },
            tickangle: 45,
            showgrid: true,
            zeroline: false,
            showline: false,
            gridcolor: "#bdbdbd",
            gridwidth: 1,
            zerolinecolor: "#969696",
            zerolinewidth: 1,
            linecolor: "#858484",
            linewidth: 1,
          },
          yaxis: {
            title: "",
            titlefont: {
              size: 12,
              color: "#000",
            },
            showgrid: true,
            zeroline: false,
            showline: false,
            gridcolor: "#bdbdbd",
            gridwidth: 1,
            zerolinecolor: "#969696",
            zerolinewidth: 1,
            linecolor: "#8b8b94",
            linewidth: 1,
          },
          legend: {
            x: 0,
            y: 1.0,
            bgcolor: "rgba(255, 255, 255, 0)",
            bordercolor: "rgba(255, 255, 255, 0)",
          },
          barmode: "group",
          bargap: 0.4,
          bargroupgap: 0,
          autosize: false,
          width: 400,
          height: 400,
          margin: {
            l: 30,
            r: 40,
            b: 120,
            t: 80,
            pad: 3,
          },
          paper_bgcolor: "#ffffff",// colore sfondo out
          plot_bgcolor: "rgba(241,241,241,0.78)", // colore sfondo in
          showlegend: false,
        },
        config: {
          displayModeBar: false,
        },
      };
    },
    watch: {
      aggregatedData: function(newData) {
        this.plotData[0].x = newData.map(row => row.key);
        this.plotData[0].y = newData.map(row => row.value);
      },
    },
  };
</script>

<style scoped>

</style>