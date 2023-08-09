<template>
  <div class="screen">
    <h1>Interact Screen</h1>
    <card-flip
        v-for="(card, index) in cardsContext"
        :key="index"
        :imgBackFaceUrl="`images/${card}.png`"
        :card="card"
        @onFlip="checkRule($event)"
    />
  </div>
</template>

<style>

</style>

<script>
import CardFlip from "@/components/Card.vue"

export default {
  props: {
    cardsContext: {
      type: Array,
      default: function () {
        return []
      }
    }
  },
  components: {
    CardFlip
  },
  data() {
    return {
      rules: [],
    }
  },
  methods: {
    checkRule(card) {
      if (this.rules.length === 2) return false;
      this.rules.push(card)
      if(this.rules.length === 2 && this.rules[0] === this.rules[1]) console.log("Right...");
      else if (this.rules.length === 2 && this.rules[0] !== this.rules[1]) console.log("Wrong...");
      else return false
    }
  }
}
</script>

