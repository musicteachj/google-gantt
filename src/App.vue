<template>
  <div id="app">
    <h1>App</h1>
    <GChart
      :settings="{ packages: ['gantt'] }"
      type="Gantt"
      :data="chartData"
      :options="chartOptions"
      ref="gChart"
    />
    <h1></h1>
  </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  name: 'app',
  components: {
    GChart
  },
  data() {
    return {
      // Array will be automatically processed with visualization.arrayToDataTable function
      chartData: [
        [
          // { type: "string", label: "Name"},
          // { type: "number", label: "Salary"},
          // { type: "boolean", label: "Full Time Employee"}
          { type: "string", label: "Task ID" },
          { type: "string", label: "Task Name" },
          { type: "date", label: "Start Date" },
          { type: "date", label: "End Date" },
          { type: "number", label: "Duration" },
          { type: "number", label: "Percent Complete" },
          { type: "string", label: "Dependencies" }, 
        ],
        ['Research', 'Find sources',
          new Date(2015, 0, 1), new Date(2015, 0, 5), null,  100,  null],
          ['Write', 'Write paper',
          null, new Date(2015, 0, 9), 259200000, 25, 'Research,Outline'],
          ['Cite', 'Create bibliography',
          null, new Date(2015, 0, 7), 86400000, 20, 'Research'],
          ['Complete', 'Hand in paper',
          null, new Date(2015, 0, 10), 86400000, 0, 'Cite,Write'],
          ['Outline', 'Outline paper',
          null, new Date(2015, 0, 6), 86400000, 100, 'Research']
        ],
     chartOptions: {
        chart: {
          title: "Company Performance",
          subtitle: "Sales, Expenses, and Profit: 2014-2017"
        }
      },
    }
  },
  methods: {
    daysToMilliseconds(days) {
      return days * 24 * 60 * 60 * 1000;
    }
  }
}
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
