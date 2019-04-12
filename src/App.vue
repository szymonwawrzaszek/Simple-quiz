<template>
   <div class="container">
     <div class="row">
       <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
         <h1 class="text-center" id="header">Anwser the question</h1>
       </div>
     </div>
     <hr>
     <div class="row">
       <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3" >
         <div style=" text-align: center;">
         </div>
         <br><br>      
         <transition mode="out-in"
         enter-active-class="animated fadeInLeft"
         leave-active-class="animated fadeOutRight">
            <component :is="comp" ></component>
         </transition>
       </div>
     </div>
   </div>
</template>

<script>
import { eventBus } from "./main";
import Answer from "./copmpnents/Answer";
import Question from "./copmpnents/Question";
export default {
  data: function() {
    return {
      comp: "app-question"
    };
  },
  components: {
    appAnswer: Answer,
    appQuestion: Question
  },
  created() {
    eventBus.$on("showAnswer", () => {
      this.comp = "app-answer";
    }),
      eventBus.$on("nextQuestion", num => {
        this.comp = "app-question";
      });
  }
};
</script>

<style >
#header {
  font-family: "Times New Roman", Times, serif;
}
.row {
}
.button {
  margin: 0 auto;
}
</style>
