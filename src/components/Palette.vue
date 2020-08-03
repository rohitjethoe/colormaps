<template>
  <div class="palette">
    <div
      class="color"
      v-for="color in colors"
      v-bind:key="color.id"
      v-bind:style="{ backgroundColor: color.hex }"
    >
      <div class="lock">
        <button class="lock-btn" @click="$emit('lock-color', color.id)">
          <span v-if="!color.locked">
            <i class="fas fa-lock-open"></i>
          </span>
          <span v-else>
            <i class="fas fa-lock"></i>
          </span>
        </button>
      </div>
      <div class="name">{{ color.name }}</div>
      <div class="hex">{{ color.hex }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Palette",
  props: ["colors"],
  methods: {
    getClass() {
      return {
        "fas fa-lock-open": !this.locked,
        "fas fa-lock": this.locked
      };
    }
  }
};
</script>

<style scoped>
.palette {
  display: flex;
  justify-content: space-evenly;
}

.color {
  display: flex;
  flex-direction: column;
  justify-content: end;
  width: 20%;
  height: calc(100vh - 60px);
  transition: 0.25s all;
  text-align: center;
  font-family: "Dosis", sans-serif;
  color: #fff;
}

.color .name,
.color .hex {
  font-size: 32px;
}

.color .hex {
  padding-bottom: 30px;
}

.lock-btn {
  color: #fff;
  font-size: 18px;
  background-color: rgba(0, 0, 0, 0);
  border: none;
  cursor: pointer;
  transition: 0.2s all;
}

.lock-btn:active {
  font-size: 24px;
}

@media only screen and (max-width: 800px) {
  .palette {
    flex-direction: column;
  }
  .color {
    width: 100%;
    height: 25vh;
  }
}
</style>