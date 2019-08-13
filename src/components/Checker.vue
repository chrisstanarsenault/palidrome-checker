<template>
  <div id="full-container">
  <div id="palindrome-wrapper">
    <div id="form-container">
      <form id="message" v-on:submit.prevent="palindromeCheck">
        <input v-model.lazy="string" id="string" name="string" placeholder="Enter a word or sentence" />
        <button>Submit</button>
        </form>
      </div>
      <span id="answer" transition=fade>{{palindrome}}{{palindromeSentence}}</span>
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
      palindromeSentence: "dont read me"
    }
  },
  methods: {
    palindromeCheck: function() {
      const stringArray = this.string.toLowerCase().split("");
      const mapString1 = stringArray.map(s => s).join().replace(/[^A-Za-z0-9]+/g, "");
      const mapString2 = stringArray.reverse().map(s => s).join().replace(/[^A-Za-z0-9]+/g, "");

      if (mapString1 == mapString2) {
        this.palindrome = this.string
        this.palindromePass = true;
        this.isTrue = true;
        this.palindromeSentence = " is a palindrome!"
      } else {
        this.palindrome = this.string
        this.palindromePass = false;
        this.isTrue = false;
        this.palindromeSentence = " is NOT a palindrome!"
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

  span {
    margin-top: 20px;
    font-size: 30px;
    visibility: hidden;
  }
</style>