<template>
  <canvas id="myChart" width="100" height="200"></canvas>
  <!-- {{server}} -->
</template>

<script>
import Vue from "vue"
import Chart from 'chart.js/auto';
import axios from 'axios'
import { isProxy, toRaw } from 'vue';
export default {
  name: 'BarChart',
  components: {  },
  computed: {
    
  },
  data() {
    return {
      labels: ['Kapital', 'ABB'],
      numberK: [],
      numberA: [],
      date: [],
      radioK: [],
      radioA: []
    }
  },
  async created(){
    // fetch('http://localhost:3000/data').
    // then(response=>response.json()).
    // then(data=>{
    //   this.server = data.values
    // }).
    // catch(err=>console.log(err.message))
    const server = await axios.get('http://localhost:3000/data')
    server.data.map(el=>{
      if(el[0] === 331){
        this.numberK.push(el[el.length-1])
      }
      else{
        this.numberA.push(el[el.length-1])
      }
    })
  },
  mounted() {
    // console.log(this.numberK)
    // let myTarget = JSON.parse(JSON.stringify(this.numberK))
    // console.log(myTarget)
    // console.log(this.numberK)
    const rawObjectOrArray = toRaw(this.numberK)
    console.log(rawObjectOrArray)
    const ctx = document.getElementById('myChart');
    const data = {
        labels: [],
        datasets: [
          {
            label: this.labels[0],
            data: [12, 19, 3, 5, 2, 3],
            borderWidth: 1
        },
        {
          label: this.labels[1],
          data: [12, 19, 3, 5, 2, 3],
        }]
    }
    const myChart = new Chart(ctx, {
    type: 'line',
    data: data,
    });
  },
}
</script>

<style scoped>
    canvas{
      height: 200px;
    }
</style>