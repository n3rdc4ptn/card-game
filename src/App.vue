<template>
  <v-app>
    <v-container v-if="showComponent != 'game'" class="fill-height" fluid>
      <v-row align="center" justify="center">
        <v-col cols="12" sm="8" md="4">
          <v-card class="mx-auto" max-width="800" min-height="500" outlined>
            <v-app-bar dark color="pink">
              <v-toolbar-title>Card Game</v-toolbar-title>

              <v-spacer></v-spacer>
            </v-app-bar>

            <v-main fluid>
              <StartScreen v-if="showComponent == 'start'" v-on:player_selected="players = $event; next()" />
              <SelectDeck v-if="showComponent == 'select'" v-on:start_game="startGame($event)" v-on:back="back()" />
            </v-main>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    <PlayGame v-if="showComponent == 'game'" :cards="cards" v-on:back_to_start="showComponent = 'start'" />
  </v-app>
</template>

<script>
import StartScreen from "./components/StartScreen";
import SelectDeck from "./components/SelectDeck";
import PlayGame from "./components/PlayGame";

Array.prototype.shuffle = function () {
  let input = this;

  for (let i = input.length - 1; i >= 0; i--) {

    let randomIndex = Math.floor(Math.random() * (i + 1));
    let itemAtIndex = input[randomIndex];

    input[randomIndex] = input[i];
    input[i] = itemAtIndex;
  }
  return input;
}

export default {
  name: "App",

  components: {
    StartScreen,
    SelectDeck,
    PlayGame
  },

  data: () => ({
    showComponent: "start",
    cards: [],
    players: []
  }),

  methods: {
    startGame(deck) {
      this.cards = deck.cards.shuffle().slice(0,20);
      this.cards.forEach(card => {
        let wcPlayer = this.players.slice();
        wcPlayer.shuffle();
        while (card.text.indexOf('%PLAYER%') >= 0) {
          card.text = card.text.replace('%PLAYER%', wcPlayer.pop() || '')
        }
      });
      this.next()
    },
    back() {
      switch (this.showComponent) {
        case "select":
          this.showComponent = "start";
          break;
        case "game":
          this.showComponent = "select";
        default:
          break;
      }
    },
    next() {
      switch (this.showComponent) {
        case "start":
          this.showComponent = "select";
          break;
        case "select":
          this.showComponent = "game";
        default:
          break;
      }
    }
  }
};
</script>
