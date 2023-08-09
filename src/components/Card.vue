<script setup>

</script>

<template>
  <div class="card">
    <div
        class="card__inner"
        @click="onToggleFlipCard"
        :class="{'is-flipped': isLipped}">
      <div class="card__face card__face__front">
        <div class="card_content">
        </div>
      </div>
      <div class="card__face card__face__back">
        <div
            class="card_content"
            :style="{
              backgroundImage: `url('@/assets/' + ${imgBackFaceUrl})`,
            }"
        ></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isLipped: false
    }
  },
  props: {
    imgBackFaceUrl: {
      type: String,
      required: true
    },
    card: {
      type: [String, Number, Array, Object],
    }
  },
  methods: {
    onToggleFlipCard() {
      this.isLipped = !this.isLipped
      if (this.isLipped) this.$emit("onFlip", this.card);
    }
  }
}
</script>

<style scoped lang="css">
.card {
  display: inline-block;
  margin-right: 1rem;
  margin-bottom: 1rem;
  width: 90px;
  height: 120px;
}

.card__inner {
  width: 100%;
  height: 100%;
  transition: transfrom 1s;
  transform-style: preserve-3d;
  cursor: pointer;
  position: relative;
}

.card__inner.is-flipped {
  transform: rotateY(-180deg);
}

.card__face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  overflow: hidden;
  border-radius: 1rem;
  box-shadow: 0 3px 10px 3px rgba(0, 0, 0, 0.2);
}

.card__face__back {
  background-color: var(--light);
  transform: rotateY(-180deg);
}

.card__face__front .card_content {
  background: url("../assets/images/icon_back.png") no-repeat center center;
  background-size: 60px 60px;
  height: 100%;
  width: 100%;
}

.card__face__back .card_content {
  background-size: contain;
  background-position: center center;
  background-repeat: no-repeat;
  height: 100%;
  height: 100%;
}
</style>