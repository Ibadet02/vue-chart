<template>
<div :class="'container'">
    <Bank1
    :server="server"
    :labelK="labels[0]"
    :date="date"
    />
    <Bank2
    :server="server"
    :dataA="dataA"
    :labelA="labels[1]"
    />
</div>
<!-- <button @click="toggleNavbar"><span v-if="!showNavbar">open</span><span v-else>close</span> navbar</button> -->

</template>


<script>
import Bank1 from './components/Bank1.vue'
import Bank2 from './components/Bank2.vue'
import server from './components/data'
export default {
    name: "App",
    components: { Bank1, Bank2 },
    data() {
        return {
            date: server.map((el, index)=>el[4]),
            server: server,
            dataA: server.filter((el, index)=>el[0]===367),
            labels: ['Kapital', 'ABB'],
            radioK: [],
            radioA: [],
        }
    },
}
</script>

<style>
    .container{
        width: 100%;
        height: 500px;
    }
</style>>
