<template>
</template>

<script>
import decks from '../assets/decks.json'

export default {
  name: "SelectDeck",
  props: {
    msg: String
  },
  data: () => ({ decks }),
  methods: {
    next(deck) {}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
