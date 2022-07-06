<template>
<div :class="'container'">
    <Bank1
    :dataK="dataK"
    :labelK="labels[0]"
    />
    <Bank2
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
            dataK: server.filter(el=>el[0]===331).map(el=>el),
            dataA: server.filter(el=>el[0]===367).map(el=>el),
            labels: ['Kapital', 'ABB'],
            radioK: [],
            radioA: []
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
