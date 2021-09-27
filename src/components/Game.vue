<template>
  <div class="main">
    <div class="words">
      <div
        class="word"
        v-for="(word, index) in words"
        :key="word"
        v-bind:class="{ highlighted: index === 0 }"
      >
        <span> {{ word }} </span>
      </div>
    </div>
    <div class="input-row">
      <input type="text" @keypress="StartTimer()" v-model="input" />
      <div class="timer">
        <span> {{ seconds }} </span>
      </div>
      <div class="restart_timer">
        <img
          src="../assets/restart1.png"
          class="restart_image"
          @click="RestartTimer()"
        />
      </div>
    </div>
  </div>
  <div class="results">
    <div class="results_header">
      <span>Result</span>
    </div>
    <div class="wpm">
      <span style="padding-right: 10px">50</span>
      <span>WPM</span>
    </div>
    <div class="accuracy">
      <span>Accuracy</span>
      <span>90%</span>
    </div>
    <div class="correct_words">
      <span>Correct words</span>
      <span style="color: green">45</span>
    </div>
    <div class="wrong_words">
      <span>Wrong words</span>
      <span style="color: red">5</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Game",
  data() {
    return {
      words: [
        "one",
        "two",
        "three",
        "four",
        "five",
        "six",
        "seven",
        "eight",
        "nine",
        "ten",
        "eleven",
        "twelve",
        "thirteen",
        "fourteen",
        "fifteen",
        "sixteen",
        "seventeen",
        "eighteen",
        "nineteen",
        "twenty",
      ],
      seconds: 60,
      input: "",
      already_started: false,
    };
  },
  methods: {
    StartTimer() {
      if (this.already_started === false) {
          setInterval(this.Proba, 1000);
      }
      this.already_started = true;
    },
    Proba() {
      this.seconds--;
      console.log("Prosla sekunda");
    },
    RestartTimer() {
      this.seconds = 60;
      this.input = "";
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Ubuntu&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Ubuntu", sans-serif;
}
body {
  display: flex;
  justify-content: center;
}
.main {
  max-width: 750px;
  height: 230px;
  margin-top: 50px;
  margin-left: 30px;
  margin-right: 30px;
  border-radius: 5px;
  padding: 20px;
  border: 2px solid grey;
}
.words {
  border: 2px solid grey;
  max-width: 700px;
  height: 80px;
  overflow: hidden;
  margin: 20px auto;
}
.word {
  display: inline-block;
  margin: 5px;
  font-size: 25px;
}
.highlighted {
  background-color: rgb(206, 241, 255);
}
input {
  width: 70%;
  height: 30px;
  font-size: 20px;
  border: none;
}
.input-row {
  max-width: 700px;
  margin: auto;
  background-color: deepskyblue;
  padding: 10px;
  display: flex;
  justify-content: space-around;
}
.timer {
  width: 15%;
  height: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 25px;
  background-color: white;
}
.results {
  border: 2px solid grey;
  margin: 30px;
  max-width: 350px;
  border-radius: 5px;
}
.results_header {
  background-color: deepskyblue;
  color: white;
  font-size: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 40px;
}
.wpm {
  color: red;
  font-size: 45px;
  font-weight: bold;
  text-align: center;
  height: 70px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.accuracy {
  background-color: rgb(206, 241, 255);
  font-size: 25px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 20px;
  padding-right: 20px;
  height: 50px;
}
.correct_words {
  font-size: 25px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 20px;
  padding-right: 20px;
  height: 50px;
}
.wrong_words {
  background-color: rgb(206, 241, 255);
  font-size: 25px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 20px;
  padding-right: 20px;
  height: 50px;
}
.restart_timer {
  background-color: white;
  width: 5%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
.restart_image {
  width: 20px;
}
</style>