<template>
  <v-container>
    
    <v-card-actions>
      <v-btn color="primary" @click="$emit('back')">Zurück</v-btn>
      <v-spacer></v-spacer>
    </v-card-actions>
  </v-container>
</template>

<script>
import _ from 'lodash';
import decks from '../assets/decks.json'

export default {
  name: "SelectDeck",
  props: {
    msg: String
  },
  data: () => ({ decks }),
  methods: {
    next(deck) {
      this.$emit('start_game', _.cloneDeep(deck))
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pointer {
  cursor: pointer;
}
</style>
