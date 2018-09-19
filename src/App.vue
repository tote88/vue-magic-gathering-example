<template>
  <div id="app">
    <div>
      <button @click="getDeck">new Deck</button>
    </div>
    <card v-for="item in cards" :key="item.id" :name="item.name" :image="item.imageUrl"></card>
  </div>
</template>

<script>
import Card from './components/card'
export default {
  name: 'App',
  components: {
    Card
  },
  data () {
    return { 
      cards: []
    }
  },
  methods: {
    getDeck: function() {
      fetch("https://api.magicthegathering.io/v1/cards?pageSize=7&random=true")
      .then((data) => data.json())
      .then(data => this.cards = data.cards)
    }
  }
}
</script>
