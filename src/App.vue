<template>
  <div id="app">
    <h1 class="headline">Cliché List</h1>
    <p class="flavour">I need to remember to achieve the following clichés:</p>
    <ClicheInput @add="addCliche"></ClicheInput>
    <ul>
      <ClicheItem
        v-for="(cliche, i) in allCliches"
        :key="cliche.id"
        :cliche="cliche"
        @delete="deleteCliche"></ClicheItem>
    </ul>
  </div>
</template>

<script>
import ClicheItem from './components/ClicheItem.vue'
import ClicheInput from './components/ClicheInput.vue'

let currentClicheId = 0;

export default {
  components: {
    ClicheItem,
    ClicheInput
  },
  methods: {
    addCliche(clicheToAdd) {
      this.allCliches.push({
        text: clicheToAdd,
        checked: false,
        id: ++currentClicheId
      });
    },
    deleteCliche(idToRemove) {
      this.allCliches = this.allCliches.filter(cliche => {
        return cliche.id !== idToRemove
      })
    }
  },
  data () {
    return {
      allCliches: [
        {
          text: "Make a to-do list knockoff with the Vue.js framework",
          checked: true,
          id: ++currentClicheId
        },
        {
          text: "Make a real web app with the Vue.js framework",
          checked: false,
          id: ++currentClicheId
        }
      ]
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Lobster|Open+Sans');

body {
  padding: 100px;
  color: #495057;
  font-size: 20px;
  font-family: 'Open Sans', sans-serif;
  line-height: 1.6em;
}

#app {
  margin: 0 auto;
  padding: 20px 0px 40px;
  max-width: 700px;
  background-color: #fff;
  box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
}

.headline {
  text-align: center;
  font-size: 72px;
  font-family: 'Lobster', sans-serif;
}

.flavour {
  margin-bottom: 40px;
  text-align: center;
}

ul {
  margin: 0;
  padding: 0;
}
</style>
