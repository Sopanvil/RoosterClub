<template>
  <div class="game">
    <div class="container">
      <div id="dice1" class="dice dice-one" :class="['show-' + firstDice]">
        <div id="dice-one-side-one" class="side one">
          <div class="dot one-1"></div>
        </div>
        <div id="dice-one-side-two" class="side two">
          <div class="dot two-1"></div>
          <div class="dot two-2"></div>
        </div>
        <div id="dice-one-side-three" class="side three">
          <div class="dot three-1"></div>
          <div class="dot three-2"></div>
          <div class="dot three-3"></div>
        </div>
        <div id="dice-one-side-four" class="side four">
          <div class="dot four-1"></div>
          <div class="dot four-2"></div>
          <div class="dot four-3"></div>
          <div class="dot four-4"></div>
        </div>
        <div id="dice-one-side-five" class="side five">
          <div class="dot five-1"></div>
          <div class="dot five-2"></div>
          <div class="dot five-3"></div>
          <div class="dot five-4"></div>
          <div class="dot five-5"></div>
        </div>
        <div id="dice-one-side-six" class="side six">
          <div class="dot six-1"></div>
          <div class="dot six-2"></div>
          <div class="dot six-3"></div>
          <div class="dot six-4"></div>
          <div class="dot six-5"></div>
          <div class="dot six-6"></div>
        </div>
      </div>
    </div>
    <div class="container">
      <div id="dice2" class="dice dice-two" :class="['show-' + secondDice]">
        <div id="dice-two-side-one" class="side one">
          <div class="dot one-1"></div>
        </div>
        <div id="dice-two-side-two" class="side two">
          <div class="dot two-1"></div>
          <div class="dot two-2"></div>
        </div>
        <div id="dice-two-side-three" class="side three">
          <div class="dot three-1"></div>
          <div class="dot three-2"></div>
          <div class="dot three-3"></div>
        </div>
        <div id="dice-two-side-four" class="side four">
          <div class="dot four-1"></div>
          <div class="dot four-2"></div>
          <div class="dot four-3"></div>
          <div class="dot four-4"></div>
        </div>
        <div id="dice-two-side-five" class="side five">
          <div class="dot five-1"></div>
          <div class="dot five-2"></div>
          <div class="dot five-3"></div>
          <div class="dot five-4"></div>
          <div class="dot five-5"></div>
        </div>
        <div id="dice-two-side-six" class="side six">
          <div class="dot six-1"></div>
          <div class="dot six-2"></div>
          <div class="dot six-3"></div>
          <div class="dot six-4"></div>
          <div class="dot six-5"></div>
          <div class="dot six-6"></div>
        </div>
      </div>
    </div>
    <div id="roll" class="roll-button">
      <button @click="rollDice">Roll dice!</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstDice: 1,
      secondDice: 1,
    };
  },
  methods: {
    rollDice() {
      this.firstDice = Math.floor(Math.random() * 6 + 1);
      this.secondDice = Math.floor(Math.random() * 6 + 1);
      console.log(this.firstDice, this.secondDice);
    },
  },
};
</script>

<style scoped>

button {
  position: relative;
  top: 80px;
  left: 10px;
  padding: 15px 50px;
  color: #fff;
  background-color: #0e0e0e;
  border: none;
  font-size: 20px;
  border-radius: 20px;
  box-shadow: 1px 3px #50514f;
  outline: none;
  transition: 0.3s;
}

button:hover{
  background: #1a1a1a;
  cursor: pointer;
}
button:active {
  outline: none;
  background: #50514f;
  cursor: pointer;
  transform: translateY(15px);
}

.game {
  display: flex;
  justify-content: center;
  position: relative;
  width: auto;
  height: 100%;
}

.container {
  position: relative;
  display: inline-block;
  top: 200px;
}

.dice {
  position: relative;
  width: 150px;
  height: 150px;
  transform-style: preserve-3d;
  transition: transform 0.3s;
}

.dot {
  position: absolute;
  width: 30px;
  height: 30px;
  margin: -15px 0px 0px -15px;
  border-radius: 20px;
  background-color: #000000;
  box-shadow: inset 3px 3px #686868;
}

.dice-one {
  position: absolute;
  left: -100px;
}

.dice-two {
  position: absolute;
  left: 150px;
}

.side {
  position: absolute;
  background-color: #fff;
  border-radius: 5px;
  width: 150px;
  height: 150px;
  border: 1px solid #e5e5e5;
  text-align: center;
  line-height: 2em;
}

.side:nth-child(1) {
  transform: translateZ(76px);
}

.side:nth-child(6) {
  transform: rotateY(90deg) translateZ(76px);
}

.side:nth-child(3) {
  transform: rotateY(-90deg) translateZ(76px);
}

.side:nth-child(4) {
  transform: rotateX(90deg) translateZ(76px);
}

.side:nth-child(5) {
  transform: rotateX(-90deg) translateZ(76px);
}

.side:nth-child(2) {
  transform: rotateY(-180deg) translateZ(76px);
}

.show-1 {
  transform: rotateX(0deg) rotateZ(0deg);
}

.show-2 {
  transform: rotateX(180deg) rotateZ(270deg);
}

.show-3 {
  transform: rotateY(90deg) rotateZ(360deg);
}

.show-4 {
  transform: rotateY(90deg) rotateZ(-90deg);
}

.show-5 {
  transform: rotateX(90deg) rotateZ(0deg);
}

.show-6 {
  transform: rotateX(90deg) rotateZ(90deg);
}

.two-1,
.three-1,
.four-1,
.five-1,
.six-1 {
  top: 20%;
  left: 20%;
}

.four-3,
.five-3,
.six-4 {
  top: 20%;
  left: 80%;
}

.one-1,
.three-2,
.five-5 {
  top: 50%;
  left: 50%;
}

.four-2,
.five-2,
.six-3 {
  top: 80%;
  left: 20%;
}

.two-2,
.three-3,
.four-4,
.five-4,
.six-6 {
  top: 80%;
  left: 80%;
}

.six-2 {
  top: 50%;
  left: 20%;
}

.six-5 {
  top: 50%;
  left: 80%;
}
</style>
