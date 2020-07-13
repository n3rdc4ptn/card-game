<template>
  <v-container>
    <v-row>
      <v-col v-for="(item, i) in decks" :key="i" cols="12">
        <v-card class="pointer" @click="next(item)" v-ripple :color="item.color" dark>
          <div class="d-flex flex-no-wrap justify-space-between">
            <div>
              <v-card-title class="headline" v-text="item.name"></v-card-title>

              <v-card-subtitle v-text="item.subtitle"></v-card-subtitle>
            </div>

            <v-avatar class="ma-3" size="125" tile>
              <fa-icon :icon="item.icon" size="6x"></fa-icon>
            </v-avatar>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
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
    next(deck) {
      this.$emit('start_game', deck)
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
