<script>
export default {
  data() {
    return {
      scoreone: 0,
      scoretwo:0,
      playing: false,
      playerChoice: "",
      computerChoice: "",
      result: "",
      gameOver: false,
      heartchoice:"heart.jpg"
    };
  },
  methods: {
    playGame() {
      const choices = ["hammerr.jpg", "paper.jpg", "scissor.jpg","heart.jpg"];
      this.playerChoice = choices[Math.floor(Math.random() * choices.length)];
      this.computerChoice = choices[Math.floor(Math.random() * choices.length)];
      this.calculateResult();
      this.playing = true;
    },
    calculateResult() {
      if (this.playerChoice === this.computerChoice) {
        this.result = "เสมอ";
      }else if(this.playerChoice === "heart.jpg"){
        this.result = "playerOne WIN";
        this.scoreone += 1;
      }
      else if(this.computerChoice === "heart.jpg"){
        this.result = "playerTwo WIN";
        this.scoretwo += 1;
      }
      else if (
        (this.playerChoice === "hammerr.jpg" && this.computerChoice === "scissor.jpg") ||
        (this.playerChoice === "paper.jpg" && this.computerChoice === "hammerr.jpg") ||
        (this.playerChoice === "scissor.jpg" && this.computerChoice === "paper.jpg")
      ) {
        this.result = "playerOne WIN";
        this.scoreone += 1;
        this.scoretwo += 0;
      } else {
        this.result = "playerTwo WIN";
        this.scoreone += 0;
        this.scoretwo += 1;
      }
    },
    resetGame() {
      this.playing = false;
      this.playerChoice = "";
      this.computerChoice = "";
      this.result = "";
      this.gameOver = false;
    },
  },
};
</script>
<template>
  <div>
    <h1>เป่ายิ๊ง...ฉุบบบบบบบบบบบบบบ</h1>
    <p>scoreplayerOne: {{ scoreone }}</p>
    <p>scoreplayerTwo: {{ scoretwo }}</p>
    <button @click="playGame" :disabled="gameOver">เริ่มเล่น</button>
    <button @click="resetGame" :disabled="!gameOver">เริ่มใหม่</button>
    <div v-if="playing">
      <h2>playerOne: <img :src="playerChoice" alt="player one Choice"></h2>
      <h2>playerTwo: <img :src="computerChoice" alt="player two Choice"> </h2>
      <h3>ผล: {{ result }}</h3>
      
    </div>
  </div>
</template>




<style scoped>
.read-the-docs {
  color: #a4f307;
}
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #03fb7baa); 
}
</style>
