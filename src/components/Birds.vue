<template>
    <div class="list">
        <h2>These are some of the birds you can spot in Vilnius</h2>
        <div v-for="bird in birds" :key="bird.name">
            <p> {{ bird.name }}: {{ bird.amount }} birds</p>
        </div>
    </div>
</template>

<script>
export default {
    // name: Birds,
    props: ['birds']
}
</script>

<style>

</style>