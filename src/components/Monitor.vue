<template>
  <div class="data row">
    <section class="col-md-6">
      <h5>Consumption</h5>
      <line-chart :chart-data="datacollection" :options="chartOptions"></line-chart>
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
    this.fillData()
    this.getLiveReadings()
  },
  data () {
    return {
      msg: 'Live Monitor',
      datacollection: null,
      chartOptions: {responsive: true, maintainAspectRatio: false},
      source1: [0, 0, 0, 0, 0, 0, 0, 0],
      source2: [0, 0, 0, 0, 0, 0, 0, 0],
      source3: [0, 0, 0, 0, 0, 0, 0, 0]
    }
  },
  methods: {
    fillData: function () {
      this.datacollection = {
        labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
        datasets: [
          {
            label: 'Meter 1',
            borderColor: '#649EB9',
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#649EB9',
            backgroundColor: 'transparent',
            data: this.source1
          },
          {
            label: 'Meter 2',
            borderColor: '#249EBF',
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#249EBF',
            backgroundColor: 'transparent',
            data: this.source2
          },
          {
            label: 'Meter 3',
            borderColor: '#FF0E00',
            pointBackgroundColor: 'white',
            borderWidth: 1,
            pointBorderColor: '#FF0E00',
            backgroundColor: 'transparent',
            data: this.source3
          }
        ]
      }
    },
    getLiveReadings: function () {
      setInterval(() => {
        this.fillData()
        console.log('Init :' + this.datacollection.datasets[0].data)
        pushData(this.source1)
        pushData(this.source2)
        pushData(this.source3)
        console.log('Even :' + this.datacollection.datasets[0].data)
      }, 1000)
    }
  }
}

function pushData (data) {
  data.push(r())
  data.shift()
}

function r () {
  return Math.floor(Math.random() * 100) + 1
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
