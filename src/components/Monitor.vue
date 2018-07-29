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
  mounted () {
    this.getLiveReadings()
  },
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
            data: [0, 0, 0, 0, 0, 0, 0]
          },
          {
            label: 'Meter 2',
            borderColor: '#249EBF',
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#249EBF',
            backgroundColor: 'transparent',
            data: [0, 0, 0, 0, 0, 0, 0]
          },
          {
            label: 'Meter 3',
            borderColor: '#FF0E00',
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#FF0E00',
            backgroundColor: 'transparent',
            data: [0, 0, 0, 0, 0, 0, 0]
          }
        ]
      },
      chartOptions: {responsive: true, maintainAspectRatio: false}
    }
  },
  methods: {
    getLiveReadings: function () {
      setInterval(() => {
        pushData(this.chartData.datasets[0].data)
        pushData(this.chartData.datasets[1].data)
        pushData(this.chartData.datasets[2].data)
      }, 5000)
    }
  }
}

function pushData (data) {
  data.push(Math.floor(Math.random() * 100) + 1)
  data.shift()
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
