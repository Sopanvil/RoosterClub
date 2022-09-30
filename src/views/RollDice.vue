<template>
  <div class="all-tem">
    <div class="wins">
      <div class="container">
        <div class="wins-title">Wins history</div>
        <div class="wins-column">

        </div>
      </div>
    </div>
    <div class="game">
      <div class="text-container">
        <p class="game-label"><span class="yellow">Roosters</span> diceroll</p>
        <p class="game-choose-label-text">
          Check number you would like too see
        </p>
        <div class="game-choose-cash">
          <input
            v-model="cashValue"
            class="game-slider"
            type="range"
            min="0.1"
            max="2"
            step="0.1"
          />
          <span class="game-range-label">{{ cashValue }}</span>
        </div>
        <div class="game-choose-number">
          <input
            v-model="rangeValue"
            class="game-slider"
            type="range"
            min="3"
            max="12"
            step="1"
          />
          <span class="game-range-label">{{ rangeValue }}</span>
        </div>
      </div>
      <div class="dice-container">
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
      </div>
      <div id="roll" class="roll-button">
        <button @click="rollDice">Roll dice!</button>
      </div>
    </div>
    <div class="history">
      <div class="container">
        <div class="history-title">Roll history</div>
        <div class="history-column">
          <div
            v-for="(item, index) in diceHistory"
            :key="index"
            class="history-dice"
          >
            <div v-if="item.win" class="history-dice-win">
              Your roll is {{ item.firstNumber }} - {{ item.secondNumber }} ({{
                item.sumNumbers
              }}) you won <span class="yellow">{{ item.winSum }}</span>
            </div>
            <div v-else class="history-dice-lose">
              Your roll {{ item.firstNumber }} - {{ item.secondNumber }} ({{
                item.sumNumbers
              }}) no dice
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
const solanaWeb3 = require('@solana/web3.js');

export default {
  data() {
    return {
      wallet: null,

      diceHistory: [],
      winSumCalculus: 0,
      winCalculus: false,

      firstDice: 1,
      secondDice: 1,
      cashValue: 0.1,
      rangeValue: 3,
      rangeValueCalculus: [
        {
          rangeNumber: 3,
          rangePercent: 0.1,
        },
        {
          rangeNumber: 4,
          rangePercent: 0.2,
        },
        {
          rangeNumber: 5,
          rangePercent: 0.5,
        },
        {
          rangeNumber: 6,
          rangePercent: 1,
        },
        {
          rangeNumber: 7,
          rangePercent: 1.2,
        },
        {
          rangeNumber: 8,
          rangePercent: 1.5,
        },
        {
          rangeNumber: 9,
          rangePercent: 2,
        },
        {
          rangeNumber: 10,
          rangePercent: 2.5,
        },
        {
          rangeNumber: 11,
          rangePercent: 3,
        },
        {
          rangeNumber: 12,
          rangePercent: 6,
        },
      ],
    };
  },
  methods: {
    async rollDice() {
      this.firstDice = Math.floor(Math.random() * 6 + 1);
      this.secondDice = Math.floor(Math.random() * 6 + 1);
      this.winCalculus = this.firstDice + this.secondDice >= this.rangeValue;

      this.rangeValueCalculus.forEach((number) => {
        if (this.rangeValue == number.rangeNumber) {
          if (this.winCalculus) {
            this.winSumCalculus = this.cashValue * number.rangePercent;
            this.winSumCalculus = parseFloat(this.winSumCalculus.toFixed(2));
          } else {
            this.winSumCalculus = 0;
          }
        }
      });

      this.diceHistory.push({
        firstNumber: this.firstDice,
        secondNumber: this.secondDice,
        sumNumbers: this.firstDice + this.secondDice,
        win: this.winCalculus,
        winSum: this.winSumCalculus,
      });

      console.log(solanaWeb3.LAMPORTS_PER_SOL);

      const rep = await window.solana.connect()
      this.wallet = rep
    //   const destKey = new solanaWeb3.PublicKey('8M9gj6xR8uvpqLrFSbvz9A2vhSvtJFfYL5yGMUNebTPz');
    //   console.log(new solanaWeb3.Connection('https://api.devnet.solana.com').getAccountInfo(destKey));

      const provider = window.solana;

      var web3 = require("@solana/web3.js");

      //Changes are only here, in the beginning
      const phantomProvider = this.wallet;
        if(!phantomProvider){
          //Urge the user to sign in(connect) again
        }
        const pubKey = await phantomProvider.publicKey;
        console.log("Public Key: ", pubKey);

        // Establishing connection
        var connection = new web3.Connection(
          web3.clusterApiUrl('devnet'),
        );

        // I have hardcoded my secondary wallet address here. You can take this address either from user input or your DB or wherever
        var recieverWallet = new web3.PublicKey("8M9gj6xR8uvpqLrFSbvz9A2vhSvtJFfYL5yGMUNebTPz");

        // Airdrop some SOL to the sender's wallet, so that it can handle the txn fee
        var airdropSignature = await connection.requestAirdrop(
          provider.publicKey,
          web3.LAMPORTS_PER_SOL,
        );

        // Confirming that the airdrop went through
        await connection.confirmTransaction(airdropSignature);
        console.log("Airdropped");

        var transaction = new web3.Transaction().add(
          web3.SystemProgram.transfer({
            fromPubkey: provider.publicKey,
            toPubkey: recieverWallet,
            lamports: web3.LAMPORTS_PER_SOL / 20 //Investing 1 SOL. Remember 1 Lamport = 10^-9 SOL.
          }),
        );

        // Setting the variables for the transaction
        transaction.feePayer = await provider.publicKey;
        let blockhashObj = await connection.getRecentBlockhash();
        transaction.recentBlockhash = await blockhashObj.blockhash;

        // Transaction constructor initialized successfully
        if(transaction) {
          console.log("Txn created successfully");
        }

        // Request creator to sign the transaction (allow the transaction)
        let signed = await provider.signTransaction(transaction);
        // The signature is generated
        let signature = await connection.sendRawTransaction(signed.serialize());
        // Confirm whether the transaction went through or not
        await connection.confirmTransaction(signature);

        //Signature or the txn hash
        console.log("Signature: ", signature);
    },
  },
};
</script>

<style lang="scss" scoped>
.all-tem {
  width: 100%;
  display: flex;
  justify-content: space-between;
  margin-top: 50px;
}
.wins {
  width: 300px;
  height: inherit;
  height: max-content;
  margin: 0 20px;
  border: 1px solid #2e2f36bd;
  box-shadow: 0 0 10px #00000015, inset 0 0 10px #2e2f3641;
  border-radius: 15px;
  .wins-title {
    display: flex;
    justify-content: center;
    font-size: 25px;
    font-weight: 600;
    margin-bottom: 10px;
  }
  .container {
    padding: 20px;
  }
}
.game {
  width: 700px;
  height: 100%;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  position: relative;
  button {
    position: relative;
    padding: 15px 50px;
    color: #0c0d11;
    background-color: #ffffff;
    border: none;
    font-size: 20px;
    border-radius: 20px;
    box-shadow: 1px 3px #50514f;
    outline: none;
    transition: 0.3s;
    &:hover {
      background: #a1a1a1;
      cursor: pointer;
    }
    &:active {
      outline: none;
      background: #cecece;
      cursor: pointer;
      transform: translateY(15px);
    }
  }
  .text-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 60px;

    .game-label {
      font-size: 60px;
      font-weight: 700;
      margin-bottom: 15px;
    }
    .game-choose-label-text {
      font-size: 40px;
      font-weight: 400;
      margin-bottom: 60px;
    }
    .game-choose-number,
    .game-choose-cash {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 30px;
      width: 320px;
      .game-slider {
        -webkit-appearance: none;
        margin-right: 15px;
        width: 250px;
        height: 7px;
        background: #15161b;
        border-radius: 5px;
        &::-webkit-slider-thumb {
          -webkit-appearance: none;
          height: 20px;
          width: 20px;
          border-radius: 50%;
          background: #ffcb00;
          cursor: ew-resize;
          box-shadow: 0 0 3px 0 #ffcb00;
          transition: background 0.3s ease-in-out;
        }

        &::-webkit-slider-runnable-track {
          -webkit-appearance: none;
          box-shadow: none;
          border: none;
          background: transparent;
        }
      }
      .game-range-label {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 45px;
        height: 35px;
        background-color: #fff;
        border-radius: 20px;
        font-size: 20px;
        font-weight: 600;
        color: #15161b;
      }
    }
  }
  .dice-container {
    width: 400px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 60px;
  }
  .container {
    position: relative;
    width: 150px;
    height: 150px;
    display: flex;
  }

  .dice {
    position: relative;
    width: 150px;
    height: 150px;
    transform-style: preserve-3d;
    transition: transform 0.8s;
  }

  .dot {
    position: absolute;
    width: 30px;
    height: 30px;
    margin: -15px 0px 0px -15px;
    border-radius: 20px;
    background-color: #000000;
  }

  .dice-one {
    position: absolute;
  }

  .dice-two {
    position: absolute;
  }

  .side {
    position: absolute;
    background-color: #fff;
    border-radius: 5px;
    box-shadow: inset 0 0 40px #686868;
    width: 150px;
    height: 150px;
    border: 1px solid #989898;
    text-align: center;
    line-height: 2em;
  }

  .side:nth-child(1) {
    transform: translateZ(74px);
  }

  .side:nth-child(6) {
    transform: rotateY(90deg) translateZ(74px);
  }

  .side:nth-child(3) {
    transform: rotateY(-90deg) translateZ(74px);
  }

  .side:nth-child(4) {
    transform: rotateX(90deg) translateZ(74px);
  }

  .side:nth-child(5) {
    transform: rotateX(-90deg) translateZ(74px);
  }

  .side:nth-child(2) {
    transform: rotateY(-180deg) translateZ(74px);
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
}
.history {
  width: 300px;
  margin: 0 20px;
  background-color: #15161b;
  border: 1px solid #2e2f36;
  box-shadow: 0 0 10px #00000015, inset 0 0 10px #2e2f3641;
  border-radius: 15px;
  .history-title {
    display: flex;
    justify-content: center;
    font-size: 25px;
    font-weight: 600;
    margin-bottom: 10px;
  }
  .container {
    padding: 20px;
    .history-column {
      display: flex;
      flex-direction: column-reverse;
    }
    .history-dice {
      padding: 10px 0;
      text-align: center;
      font-size: 15px;
      font-weight: 300;
      border-bottom: 1px solid #2e2f36;
    }
  }
}
</style>
