<style>

</style>

<template>
  <main-screen
      v-if="statusMath === 'default'"
      @selectMode="onHandleBeforeStart($event)"/>
  <interact-screen
      v-if="statusMath === 'match'"
      :cards-context="setting.cardsContext"/>
</template>

<script>
import MainScreen from "@/components/MainScreen.vue";
import InteractScreen from "@/components/InteractScreen.vue";

import {shuffled} from "@/assets/utils/array"

export default {
  name: "App",
  data() {
    return {
      setting: {
        totalOfBlock: 0,
        cardsContext: [],
        startAt: null
      },
      statusMath: "default",
    }
  },
  components: {
    MainScreen,
    InteractScreen
  },
  methods: {
    onHandleBeforeStart(mode) {
      console.log("Start game with mode: ", mode)
      //prepare data
      this.setting.totalOfBlock = mode.totalOfBlock
      const firstCard = Array.from({length: this.setting.totalOfBlock / 2},
          (_, i) => i+1);
      const secondCard = [...firstCard]
      const card = [...firstCard, ...secondCard]
      this.setting.cardsContext = shuffled(shuffled(shuffled(shuffled(card))))
      this.setting.startAt = new Date().getTime();
      this.statusMath = "match";
    }
  }
}
</script>
