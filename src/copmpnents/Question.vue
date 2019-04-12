<template>
    <div class="container">
        {{questions[generateNum].text}}
        <hr>
        <div style="display: inline-block;">
            <div>
                <button class="btn btn-primary button" @click="check(1)">{{questions[num].btn1}}</button>
                <button class="btn btn-primary button" @click="check(2)">{{questions[num].btn2}}</button>
            </div>
            <div style="clear: both; display: block;">
                <button class="btn btn-primary button" @click="check(3)">{{questions[num].btn3}}</button>
                <button class="btn btn-primary button" @click="check(4)">{{questions[num].btn4}}</button>
            </div>
        </div>
    </div>
</template>

<script>
import { eventBus } from "./../main";

export default {
  data: function() {
    return {
      questions: [
        {
          text: "5-3",
          btn1: "1",
          btn2: "2",
          btn3: "3",
          btn4: "4",
          correct: 2
        },
        {
          text: "2+1",
          btn1: "1",
          btn2: "2",
          btn3: "3",
          btn4: "4",
          correct: 3
        },
        {
          text: "10!",
          btn1: "1",
          btn2: "2",
          btn3: "3",
          btn4: "3628800",
          correct: 4
        },
        {
          text: "2-1",
          btn1: "1",
          btn2: "2",
          btn3: "3",
          btn4: "4",
          correct: 1
        }
      ],
      num: 0
    };
  },
  methods: {
    check(answer) {
      if (this.questions[this.num].correct == answer) {
        eventBus.$emit("showAnswer");
      } else {
        alert("Nope");
      }
    }
  },
  computed: {
    generateNum() {
      return (this.num = Math.floor(Math.random() * this.questions.length));
    }
  }
};
</script>

<style scoped>
.container {
  width: 400px;
  height: 300px;
  background: rgb(118, 133, 118);
  margin: auto;
  text-align: center;
  padding: 20px;
  font-size: 30px;
}
.button {
  width: 70px;
  height: 40px;
  margin: 20px 20px 20px 20px;
}
</style>
