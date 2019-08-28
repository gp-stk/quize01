<template>
  <div class="result">
    <p>{{ length }}問中{{ correct }}問正解です。</p>
    <p v-if="correct == 3">おめでとう。</p>
    <p v-if="correct == 0">残念でした。</p>
  </div>
</template>

<script>
export default {
  name: "Result",
  props: {
    correct: Number,
    length: Number
  }
}
</script>

<style lang="scss">
.result {
  width: 100%;
  padding: 160px 0;
  text-align: center;
  position: absolute;
  top: 0;
  left: 0;
  p {
    font-size: 28px;
    color: #fff;
    margin: 0 0 10px;
  }
}

@media (max-width: 750px) {
  .result {
    p {
      font-size: 24px;
    }
  }
}
</style>