<template>
    <h2>{{labelA}}</h2>
    <canvas id="myChart2" width="100%"></canvas>
</template>

<script>
import Chart from 'chart.js/auto';
export default {
    name: 'Bank2',
    data(){
        return {
            label: this.labelA,
            numberA: this.dataA.map(el=>el[el.length-1]),
            date: this.dataA.map(el=>el[4]),
            radioA: [...new Set(this.dataA.map(el=>el[3]))],
            colors: ['#FF2D00','#FFE400','#78FF00','#00FF64','#00FFDC','#0083FF','#0800FF','#FF00E8']
        }
    },
    props: ['labelA','dataA'],
    mounted() {
    const ctx = document.getElementById('myChart2');
    const labels = this.labels;
    const data = {
      labels: this.date,
      datasets: this.radioA.map((el,index)=>{
        let spaceFromLeft = []
        this.dataA.every(e=>e[3] === el ? false : spaceFromLeft.push('x'))
        return {
            label: el,
            data: [...Array(spaceFromLeft.length).fill(null),...this.dataA.filter(e=>e[3] === el).map(e=>e[e.length-1])],
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
  }
}
</script>

<style scoped>
    h2{
        text-align: center;
    }
</style>