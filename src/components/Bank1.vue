<template>
  <h2>{{labelK}}</h2>
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
      numberK: this.dataK.map(el=>el[el.length-1]),
      date: this.dataK.map(el=>el[4]),
      radioK: [...new Set(this.dataK.map(el=>el[3]))],
      colors: ['#FF0000','#FFFF00','#00FF00','#0800FF']
    }
  },
  props: ['labelK','dataK'],
  mounted() {
    const ctx = document.getElementById('myChart');
    const labels = this.labels;
    const data = {
      labels: this.date,
      datasets: this.radioK.map((el,index)=>{
        let spaceFromLeft = []
        this.dataK.every(e=>e[3] === el ? false : spaceFromLeft.push('x'))
        return {
            label: el,
            data: [...Array(spaceFromLeft.length).fill(null),...this.dataK.filter(e=>e[3] === el).map(e=>e[e.length-1])],
            fill: false,
            borderColor: this.colors[index],
            tension: 0.1
        }
      })
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