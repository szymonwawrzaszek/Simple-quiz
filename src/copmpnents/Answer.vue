<template>
    <div class="container" @click="click">
        Yey <br>
        Success!!!<br>  
        Click on me
    </div>
</template>

<script>
import { eventBus } from "./../main";

export default {
  data: function() {
    return {};
  },
  methods: {
    click() {
      eventBus.$emit("nextQuestion", 1);
    }
  }
};
</script>

<style scoped>
.container {
  width: 400px;
  height: 200px;
  background: lightgreen;
  margin: auto;
  text-align: center;
  padding: 50px;
  font-size: 30px;
}
</style>

