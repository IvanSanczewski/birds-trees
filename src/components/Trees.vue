<template>
    <div class="list">
        <h2>These are the most common trees of Vilnius</h2>
        <div v-for="tree in trees" :key="tree.name">
            <p> {{ tree.name }}: {{ tree.amount }} trees - 
            <span class="area" @click="displayNeighbourhood(tree.name)">Neighbourhood:</span></p>
        </div>
    </div>
</template>

<script>

export default {
    // name: Trees,
    props: ['trees', 'areas'], 
    methods: {
        displayNeighbourhood(tree) {
            this.$emit('area', tree)
        }
    }
}
</script>

<style>

</style>    