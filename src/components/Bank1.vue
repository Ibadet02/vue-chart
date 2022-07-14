<template>
  <h2>Date</h2>
  <canvas id="myChart" width="100%"></canvas>
</template>

<script>
import Chart from 'chart.js/auto';
export default {
  name: 'Bank1',
  components: {  },
  computed: {
  },
  data() {
    return {
      label: this.labelK,
      number: this.server.map(el=>el[el.length-1]),
      colors: ['#FF0000','#FFFF00','#00FF00','#0800FF']
    }
  },
  props: ['labelK','server', 'date'],
  mounted() {
    const ctx = document.getElementById('myChart');
    const labels = this.labels;
    const data = {
      labels: this.date,
      datasets: 
        // let spaceFromLeft = []
        // this.data.every(e=>e[3] === el ? false : spaceFromLeft.push('x'))
        // return {
          [{
            label: 'By date',
            data: [...this.server.map(el=>el[el.length-1])],
            fill: false,
            // borderColor: this.colors[index],
            tension: 0.1
          }]
    };
    const myChart = new Chart(ctx, {
    type: 'line',
    data: data,
    });
  },
}
</script>

<style scoped>
    h2{
      text-align: center;
    }
</style>