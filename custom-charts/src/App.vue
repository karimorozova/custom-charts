<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <DonutChart/>
  <LineBarChart />
  <PieChart/>
   <SemiDonutChart/>
</template>

<script>
import DonutChart from './components/DonutChart.vue'
import LineBarChart from './components/LineBarChart.vue'
import PieChart from './components/PieChart.vue'
import SemiDonutChart from './components/SemiDonutChart.vue'

export default {
  name: 'App',
  components: {
    DonutChart,
    LineBarChart,
    PieChart,
    SemiDonutChart
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
