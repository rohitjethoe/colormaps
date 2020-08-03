<template>
  <div class="header">
    <div class="logo">Colormaps.</div>
    <div class="nav">
      <ul>
        <li>
          <a class="generate" v-on:click="changeColors" v-on:keyup.space="changeColors">Roll Colors</a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  methods: {
    changeColors() {
      this.$emit("change-colors", true);
    }
  }
};
</script>

<style scoped>
.header {
  border-bottom: 4px solid #38456a;
}

.logo {
  font-family: "Dosis", sans-serif;
  text-transform: uppercase;
  font-size: 28px;
  color: #38456a;
  padding: 10px;
  float: left;
}

.nav {
  float: right;
  padding: 10px;
}

.nav .generate {
  font-family: "Dosis", sans-serif;
  border-bottom: 2.5px solid #38465a;
  padding-bottom: 1px;
  color: #38465a;
  font-size: 20px;
  cursor: pointer;
  transition: 0.15s all;
}

.nav .generate:active {
  color: #65686e;
  border-bottom-color: #65686e;
}

.nav .generate::selection {
  background-color: #ffffff;
  color: #38465a;
}

.header::after {
  clear: both;
  content: "";
  display: table;
}

.nav ul {
  display: inline;
  display: flex;
}

.nav ul li {
  list-style-type: none;
  margin: 0 20px;
}
</style>