<template>
  <div class="hello">
    <h6>{{ msg }}</h6>
    <line-chart :data="chartData" :options="chartOptions"></line-chart>

  </div>
</template>

<script>
import LineChart from '../components/LineChart.js'

export default {
  components: { LineChart },
  name: 'Monitor',
  data () {
    return {
      msg: 'Live Monitor',
      chartData: {
        labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
        datasets: [
          {
            label: 'Meter 1',
            backgroundColor: '#f87979',
            data: [0, 19, 10, 4, 9, 40, 10]
          },
          {
            label: 'Meter 2',
            backgroundColor: '#d87009',
            data: [40, 39, 10, 40, 39, 80, 40]
          },
          {
            label: 'Meter 3',
            backgroundColor: '#f8a97b',
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
