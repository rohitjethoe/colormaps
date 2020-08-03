<template>
  <div id="app">
    <Header v-on:change-colors="changeColors" />
    <Palette v-bind:colors="colors" v-on:lock-color="lockColor" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Palette from "./components/Palette";
const ntc = require("ntcjs");

export default {
  name: "App",
  data() {
    return {
      colors: [
        {
          id: 0,
          name: "Jet",
          hex: "#2F2F2F",
          locked: false
        },
        {
          id: 1,
          name: "Shimmering Blush",
          hex: "#DC7F9B",
          locked: false
        },
        {
          id: 2,
          name: "Carnation Pink",
          hex: "#F7A1C4",
          locked: false
        },
        {
          id: 3,
          name: "Baby Pink",
          hex: "#E0B7B7",
          locked: false
        },
        {
          id: 4,
          name: "Cambridge Blue",
          hex: "#94BFA7",
          locked: false
        }
      ]
    };
  },
  components: {
    Header,
    Palette
  },
  methods: {
    changeColors() {
      const symbols = "0123456789ABCDEF";

      var color = new Array();

      for (var i = 0; i < 6; i++) {
        color[i] = "#";
        for (var z = 0; z < 6; z++) {
          color[i] = color[i] + symbols[Math.floor(Math.random() * 16)];
        }
        if (this.colors[i].locked === false) {
          this.colors[i].hex = color[i];
          this.colors[i].name = ntc.name(color[i])[1];
        } else {
          // do nothing.
        }
      }
    },

    lockColor(id) {
      this.colors[id].locked = !this.colors[id].locked;
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

.app {
  color: #f3f3f3;
}

@import url("https://fonts.googleapis.com/css2?family=Dosis:wght@500;600&display=swap");
</style>
