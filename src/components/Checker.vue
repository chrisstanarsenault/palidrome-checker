<template>
  <div id="full-container">
    <div id="palindrome-wrapper">
      <div id="form-container">
        <form id="message" v-on:submit.prevent="palindromeCheck">
          <input v-model.lazy="string" id="string" name="string" placeholder="Enter a word or sentence" />
          <button>Submit</button>
          </form>
        </div>
        <transition name="fade">
          <span v-if="true" id="answer"><span id="highlight" class="highlight">{{palindrome}}</span>{{palindromeSentence}}</span>
        </transition>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Checker',
  data() {
    return {
      string: "",
      palindrome: "",
      palindromePass: false,
      isTrue: false,
      palindromeSentence: "if you can see me, we have a problem here",
      wordsThatArePalindromes: []
    }
  },
  methods: {
    palindromeCheck: function() {
      const stringArray = this.string.toLowerCase().split("");
      const mapString1 = stringArray.map(s => s).join().replace(/[^A-Za-z0-9]+/g, "");
      const mapString2 = stringArray.reverse().map(s => s).join().replace(/[^A-Za-z0-9]+/g, "");
      let element = document.getElementById("highlight");

      if (stringArray == "") {
        this.palindrome = "";
        this.palindromeSentence = "You didnt even enter anything!";
        element.classList.remove("highlight");
      } else if (mapString1 == mapString2) {
        this.palindrome = this.string
        this.palindromePass = true;
        this.isTrue = true;
        this.palindromeSentence = " is a palindrome!";
        this.wordsThatArePalindromes.push(this.palindrome);
        element.className="highlight";
      } else {
        this.palindrome = this.string
        this.palindromePass = false;
        this.isTrue = false;
        this.palindromeSentence = " is NOT a palindrome!"
        element.className="highlight";
      }
      document.getElementById("answer").style.visibility = "visible"
      this.string="";
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #full-container {
    margin-top: 100px;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%)
  }

  #palindrome-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 300px;
    width: 1000px;
    background-color: rgb(231, 231, 231);
    border: 1px solid black;
    border-radius: 5px;

  }

  #message {
    display: flex;
    flex-direction: column;
  }

  input {
    width: 400px;
    height: 40px;
    font-size: 20px;
    padding: 0 1rem;
    margin-bottom: 20px;
    border: 1px solid black;
    border-radius: 5px;
  }

  button {
    background-color: lightgreen;
    color: white;
    font-size: 20px;
    margin-left: 115px;
    margin-top: -8px;
    height: 60px;
    width: 200px;
    border-radius: 10px;
    border: 1px solid green;
  }

  #answer {
    margin-top: 20px;
    font-size: 30px;
    visibility: hidden;
  }

  .fade-enter-active, .fade-leave-active {
    transition: all 0.3s ease;
  }

  .fade-enter, .fade-leave-to {
    opacity: 0;
    transform: scale(0);
  }

  .highlight {
    background-color: yellow;
    padding: 0 10px;
  }
</style>