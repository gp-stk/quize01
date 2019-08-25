<template>
  <div id="app">
    <div class="quiz">
      <p class="number">第{{ current }}問</p>
      <p class="question">{{ questions[current - 1].question }}</p>
      <ul>
        <li v-on:click="selectAnswer" v-for="(question, index) in questions[current - 1].answers"><span>{{ index + 1 }}</span>{{ question }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
// import App from './components/AnswerButton.vue'

export default {
  name: 'app',
  data: function(){
    return {
      correctAnswer: 0,
      current: 1,
      questionLength: 3,
      questions: [
        {
          question: "ノンカロリーは何カロリー？",
          answers: [
            "0カロリー",
            "5キロカロリー未満",
            "10キロカロリー未満"
          ],
          answer: 2
        },
        {
          question: "つぎのうちで肉の焼き加減を表す言葉はどれ？",
          answers: [
            "イエロー",
            "レッド",
            "ブルー"
          ],
          answer: 3
        },
        {
          question: "チキンナゲットのナゲットって何？",
          answers: [
            "ねりもの",
            "判子（ハンコ）",
            "金塊"
          ],
          answer: 3
        }
      ]
    }
  },
  methods: {
    selectAnswer: function(){
      this.current ++;
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
