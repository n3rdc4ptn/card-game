<template>
  <v-container>
    <v-combobox
      v-model="players"
      label="Players"
      hint="Mindestens 2 Spieler angeben"
      persistent-hint
      multiple
      chips
    >
      <template v-slot:selection="data">
        <v-chip
          :key="JSON.stringify(data.item)"
          v-bind="data.attrs"
          :input-value="data.selected"
          :disabled="data.disabled"
          close
          @click:close="data.parent.selectItem(data.item)"
        >
          <v-avatar class="accent white--text" left v-text="data.item.slice(0, 1).toUpperCase()"></v-avatar>
          {{ data.item }}
        </v-chip>
      </template>
    </v-combobox>

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
