<template>
  <div id="app" class='calc-container'>
    <input type="text" name="" id="display" disabled :value="x"><br>
    <CalcButton v-for="digit in digits" :buttonValue="digit" :key="digit" v-model="y" :value="digit"/>
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
      digits:[7,8,9,'/','C',
              4,5,6,'*','=',
              1,2,3,'-',
              0,'.','+'],
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
      switch(this.calculationSign){
        case "+":{
          this.plus();
          break;
        }
        case "-":{
          this.minus();
          break;
        }
        case "*":{
          this.multiply();
          break;
        }
        case "/":{
          this.devine();
          break;
        }
        default:{
          this.outcome = parseFloat(this.a);
        }
      }
      this.x = this.outcome.toString();
    },
    clearData(){
      this.a = 0;
      this.b = 0;
      this.x = "";
      this.y = "";
      this.outcome = "";
    },
    plus(){
      this.outcome = this.a + this.b;
    },
    minus(){
      this.outcome = this.a - this.b;
    },
    multiply(){
      this.outcome = this.a * this.b;
    },
    devine(){
      this.outcome = this.a / this.b;
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
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
