<template>
  <div id="palindrome-wrapper">
    <div id="form-container">
      <form id="message" v-on:submit.prevent="onSubmit">
        <input v-model.lazy="string" id="string" name="string" placeholder="Enter a word or sentence" />
        <button>Submit</button>
        </form>
      </div>
      <span transition=fade>{{palindrome}}{{palindromeSentence}}</span>
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
      palindromeSentence: ""
    }
  },
  methods: {
    onSubmit: function() {
      this.palindrome = this.string;
      this.palindromeCheck()
    },
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
      this.string="";
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #palindrome-wrapper {
    padding: 20rem;
  }

  #form-container {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  input {
    width: 400px;
    height: 40px;
    font-size: 20px;
    margin-bottom: 20px;
    border: 1px solid black;
    border-radius: 5px;
  }

  button {
    background-color: lightgreen;
    color: white;
    font-size: 20px;
    margin-left: 10px;
    margin-top: -8px;
    position: absolute;
    height: 60px;
    width: 200px;
    border-radius: 10px;
    border: 1px solid green;
  }

  span {
    margin-top: 10px;
    font-size: 30px;
    transition: all 1s ease;
  }

  .fade-transition {
    transition: all 1s ease;
  }

  .fade-enter, .fade-leave {
    opacity: 1;
  }
</style>