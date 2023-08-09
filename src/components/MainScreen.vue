<template>
  <div class="screen">
    <h1>POKE MEMORIES</h1>
    <h3>Select mode to start game</h3>
    <div class="actions">
      <button @click="selectMode(16)">
        <span>4x4</span>
        <span>Easy</span>
      </button>
      <button @click="selectMode(36)">
        <span>6x6</span>
        <span>Normal</span>
      </button>
      <button @click="selectMode(64)">
        <span>8x8</span>
        <span>Hard</span>
      </button>
      <button @click="selectMode(100)">
        <span>10x10</span>
        <span>Super Hard</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    selectMode(totalOfBlock) {
      this.$emit("selectMode", {totalOfBlock})
    }
  }
}
</script>


<style>
</style>
