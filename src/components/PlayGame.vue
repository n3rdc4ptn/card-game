<template>
  <v-carousel height="100%" hide-delimiters show-arrows-on-hover>
    <v-carousel-item v-for="(card, i) in cards" :key="i">
      <v-sheet height="100%" :color="card.color" :style="card.textcolor ? `color:${card.textcolor};` : null" tile>
        <v-row class="fill-height" align="center" justify="center">
          <div class="textContainer text" >{{ card.text }}</div>
        </v-row>
        <v-row class="mt-n15" align="end" justify="center">
          <div class="cardNumber">{{ i+1 }} / {{ cards.length }}</div>
          <v-btn class="ml-5" v-text="i == cards.length-1 ? 'Zurück zum Start' : 'Abbrechen'" @click="$emit('back_to_start')"></v-btn>
        </v-row>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  name: "PlayGame",
  props: {
    msg: String,
    cards: Array
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.textContainer {
  flex: 1;
  align-items: center;
  justify-content: center;
  padding: 80px;
  max-width: 800px;
}

.text {
  color: "#fff";
  font-weight: 370;
  text-align: center;
  font-size: x-large;
}

.cardNumber {
  color: "#fff";
  font-weight: 370;
  text-align: center;
  font-size: x-large;
}

@media only screen and (min-width: 600px) {
    .text { 
        font-size: xx-large;  
    }
}

</style>
