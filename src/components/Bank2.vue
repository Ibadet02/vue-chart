<template>
    <h2>Name</h2>
    <canvas id="myChart2" width="100%"></canvas>
</template>

<script>
import Chart from 'chart.js/auto';
export default {
    name: 'Bank2',
    data(){
        return {
            // #0083FF
            label: this.labelA,
            numberA: this.dataA.map(el=>el[el.length-1]),
            bankNames: this.server.map(el=>el[1]),
            radioA: [...new Set(this.dataA.map(el=>el[3]))],
            colors: ['#FF0000','#0083FF','#FFFF00','#00FF64','#00FFDC','#00FF00','#0800FF','#FF00E8']
        }
    },
    props: ['labelA','dataA','server'],
    mounted() {
    const ctx = document.getElementById('myChart2');
    const labels = this.labels;
    const data = {
      labels: this.bankNames,
      datasets: [{
            label: 'By name',
            data: [...this.server.map(el=>el[el.length-1])],
            fill: false,
            tension: 0.1
        }]
    };
    const myChart = new Chart(ctx, {
    type: 'line',
    data: data,
    });
  }
}
</script>

<style scoped>
    h2{
        text-align: center;
    }
</style>