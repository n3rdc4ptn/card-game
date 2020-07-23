<template>
  <v-container>
    

    <v-card-actions>
      <v-spacer></v-spacer>
      <v-btn color="primary" @click="next()">Weiter</v-btn>
    </v-card-actions>
  </v-container>
</template>

<script>
export default {
  name: "StartScreen",
  props: {
    msg: String
  },
  data() {
    return {
      players: []
    };
  },
  methods: {
    next() {
      if (this.players.length > 1) {
        this.$emit("player_selected", this.players);
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
