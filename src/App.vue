<template>
  
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
    startGame(deck) {},
    back() {},
    next() {}
  }
};
</script>
