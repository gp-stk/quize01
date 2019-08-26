<template>
  <div id="app">
    <div class="box">
      <div class="quiz" v-bind:class="{ finish: isFinish }">
        <p class="number">第{{ current + 1 }}問</p>
        <p class="question">{{ questions[current].question }}</p>
        <ul class="answers">
          <li v-on:click="selectAnswer(index)" v-for="(question, index) in questions[current].answers" v-bind:key="question.id">
            <span class="num">{{ index + 1 }}</span>
            <span class="text">{{ question }}</span>
          </li>
        </ul>
      </div>
      <transition name="fade">       
        <Result v-bind:correct="correctAnswer" v-bind:length="questionLength" v-if="isFinish"></Result>
      </transition>
    </div>
  </div>
</template>

<script>
import Result from './view/Result.vue'

export default {
  name: 'app',
  data: function(){
    return {
      correctAnswer: 0,
      current: 0,
      questionLength: 3,
      isFinish: false,
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
  components: {
    Result
  },
  methods: {
    selectAnswer: function(index){
      // 正解数
      if(index == this.questions[this.current].answer - 1){
        this.correctAnswer ++
      }
      //
      if(this.current == this.questionLength - 1){
        this.isFinish = true
      } else {
        this.current ++
      }
    }
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background: #2f89fc;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.box {
  background: #fff;
  width: 100%;
  max-width: 600px;
  min-height: 400px;
  padding: 40px;
  margin: 50px auto;
  border-radius: 10px;
  position: relative;
}
.quiz {
  text-align: center;
  &.finish {
    display: none;
  }
  .number {
    font-size: 20px;
    margin: 0 0 20px;
  }
  .question {
    font-size: 24px;
    margin: 0 0 40px;

  }
}
.answers {
  margin: 0;
  padding: 0;
  li {
    list-style: none;
    background: #eee;
    text-align: left;
    margin: 0 0 10px;
    cursor: pointer;
    display: flex;
    border-radius: 10px;
    overflow: hidden;
    span {
      font-size: 18px;
      line-height: 50px;
    }
    .num {
      color: #fff;
      background: #000;
      width: 50px;
      text-align: center;
    }
    .text {
      padding: 0 20px;
    }
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 1.5s;
}
.fade-enter, .fade-leave-to  {
  opacity: 0;
}


@media (max-width: 750px) {
  #app {
    padding: 10px;
  }
  .box {
    margin: 0;
    padding: 25px;
  }
  .quiz {
    .number {
      font-size: 16px;
      margin: 0 0 10px;
    }
    .question {
      font-size: 18px;
      margin: 0 0 30px;

    }
  }
  .answers {
    li {
      span {
        font-size: 15px;
      }
      .text {
        padding: 0 15px;
      }
    }
  }
}

</style>
