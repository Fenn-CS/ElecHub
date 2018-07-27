<template>
  <div class="data row">
    <section class="col-md-6">
      <h5>Consumption</h5>
      <line-chart :data="chartData" :options="chartOptions"></line-chart>
    </section>
    <section class="data col-md-6">
      <h5>Line Observation</h5>
      <bubble-chart ></bubble-chart>
    </section>
  </div>
</template>

<script>
import LineChart from '../components/LineChart.js'
import BubbleChart from '../components/BubbleChart.js'

export default {
  components: { LineChart, BubbleChart },
  name: 'Monitor',
  data () {
    return {
      msg: 'Live Monitor',
      chartData: {
        labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
        datasets: [
          {
            label: 'Meter 1',
            borderColor: '#649EB9',
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#649EB9',
            backgroundColor: 'transparent',
            data: [0, 19, 10, 4, 9, 40, 10]
          },
          {
            label: 'Meter 2',
            borderColor: '#249EBF',
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#249EBF',
            backgroundColor: 'transparent',
            data: [40, 39, 10, 40, 39, 80, 40]
          },
          {
            label: 'Meter 3',
            borderColor: '#FF0E00',
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#FF0E00',
            backgroundColor: 'transparent',
            data: [0, 30, 19, 35, 60, 22, 0]
          }
        ]
      },
      chartOptions: {responsive: true, maintainAspectRatio: false}
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}

</style>
