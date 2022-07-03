<template>
<div :class="'container'">
    <BarChart />
</div>
<!-- <button @click="toggleNavbar"><span v-if="!showNavbar">open</span><span v-else>close</span> navbar</button> -->

</template>


<script>
import BarChart from './components/BarChart.vue'
export default {
    name: "App",
    components: { BarChart },
    data() {
        return {
            
        }
    },
    methods: {

    }
}
</script>

<style>
    .container{
        width: 500px;
        height: 300px;
    }
</style>>
