<template>
  <v-carousel height="100%" hide-delimiters show-arrows-on-hover>
    
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
