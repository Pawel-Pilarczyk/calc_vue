<template>
  <div id="app">
    <input type="text" name="" id="display" disabled :value="x">
    <CalcButton v-for="digit in digits" :buttonValue="digit" :key="digit" v-model="y"/>
  </div>
</template>

<script>


import CalcButton from './components/button';

export default {
  name: 'App',
  components: {
    CalcButton
  },
  data() {
    return {
      digits:[0,1,2,3,4,5,6,7,8,9,'+','-','=','*','/','.','C'],
      a : 0,
      b : 0,
      calculationSign :'',
      outcome:'',
      x:'',
      y :''
    }
  },
  methods: {
    addDigit: function(digit){
       this.x = this.x.concat(digit);
    },
    assignSign(){
      this.a = parseFloat(this.x);
      this.x = "";
      this.calculationSign = this.y;
    },
    equal(){
      this.b = parseFloat(this.x);
      this.outcome = this.a + this.b;
      this.x = this.outcome.toString();
    },
    clearData(){
      this.a = 0;
      this.b = 0;
      this.x = "";
      this.y = "";
      this.outcome = "";
    }
  },
  watch:{
    y(){

      if( this.y == "+" ||
          this.y == "-" ||
          this.y == "*" ||
          this.y == "/"
      ){

        this.assignSign();

      }else if(this.y == "="){

        this.equal();

      }else if(this.y === 'C'){

        this.clearData();

      }else{

         if(this.x === "" && this.y === "."){

           this.addDigit('0.');
        }else if(this.x.includes('.') && this.y === "."){

           this.x = this.x;

         }else{

            this.addDigit(this.y);

         }
      }

      this.y = "";

    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
