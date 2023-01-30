<template>
  <h1>Birds & Trees from Vilnius </h1>
  <button @click="toggleDisplayList('birds')"> Birds</button>
  <button @click="toggleDisplayList('trees')"> Trees</button>

  <form>
    <label> Select an area: </label>
    <select v-model="area">
      <option value="antakalnis">Antakalnis</option>
      <option value="markuciai">Markučiai</option>
      <option value="uzupis">Uzupis</option>
    </select>
  </form>

  <Birds v-show="displayBirds"
    :birds="birds" />

  <Trees v-show="displayTrees"
    :trees="trees"
    :areas="areas"
    @area="displayArea" />

</template>

<script>
import Birds from '@/components/Birds.vue'
import Trees from '@/components/Trees.vue'

export default {


  name: 'App',
  components: {
    Birds, Trees
  }, 
  data() {
    return {
      trees:[
        {name: 'azuolas', amount: 323},
        {name: 'egle', amount: 512},
        {name: 'berzas', amount: 489}
      ],
      birds:[
        {name: 'Grey Tit', amount: 750},
        {name: 'Crow', amount: 285},
        {name: 'Sparrow', amount: 1230}
      ],
      areas:[
        {name: 'uzupis', trees: {azuolas: 35, egle: 60, berzas: 105}},
        {name: 'antakalnis', trees: {azuolas: 155, egle: 190, berzas: 89}},
        {name: 'markuciai', trees: {azuolas: 22, egle: 85, berzas: 12}},
      ],
      area: '',
      displayBirds: false,
      displayTrees: false
    }
  },
  methods: {
    toggleDisplayList(item) {
      if (item === 'birds') {
        this.displayBirds = !this.displayBirds
      }
      if (item === 'trees') {
        this.displayTrees = !this.displayTrees
      }
    },
    displayArea(tree) {
      console.log(tree)


      console.log(this.area)
      // let requestedAreaTrees = this.areas.find(area => area.name === this.area)
      let requestedAreaTrees = [this.areas.find(area => area.name === this.area)]
      let totalTrees = requestedAreaTrees.trees.map(item => console.log(item))


      
      // console.log(requestedAreaTrees)
      // console.log(requestedAreaTrees.name)
      // console.log(requestedAreaTrees.trees)
      // console.log(requestedAreaTrees.trees.egle)
      // console.log(requestedAreaTrees.trees.azuolas)
      // console.log(requestedAreaTrees.trees.berzas)
      
      
      
      console.log(totalTrees)
      
      
      // console.log(requestedAreaTrees[0].name)
      // console.log(requestedAreaTrees[0].trees)
      
      
      // let totalAreaTrees = requestedAreaTrees.trees.filter(tree => console.log(tree))
      // console.log(totalAreaTrees)

    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  
  font-size: larger;
  
}

button {
  margin: 1em;
  padding: .5em 1em;
  
  font-size: large;
}

h1, h2 {
  margin-top: 1.5em;
}

p {
  color: rgb(80, 80, 80)
}

select {
  padding: .1em .3em
}

.area {
  color: darkgreen;
  cursor: pointer;
}
</style>
