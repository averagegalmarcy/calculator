<template>
  <div class="calculator">
    <div class="display"> {{current || '0'}} </div>
    <div @click="clear" class="button"> C </div>
    <div @click="sign" class="button"> +/- </div>
    <div @click="percent" class="button"> % </div>
    <div @click="divide" class="button operator"> ÷ </div>
    <div @click="append('7')" class="button"> 7 </div>
    <div @click="append('8')" class="button"> 8 </div>
    <div @click="append('9')" class="button"> 9 </div>
    <div @click="times" class="button operator"> x </div>
    <div @click="append('4')" class="button"> 4 </div>
    <div @click="append('5')" class="button"> 5 </div>
    <div @click="append('6')" class="button"> 6 </div>
    <div @click="minus" class="button operator"> - </div>
    <div @click="append('1')" class="button"> 1 </div>
    <div @click="append('2')" class="button"> 2 </div>
    <div @click="append('3')" class="button"> 3 </div>
    <div @click="add" class="button operator"> + </div>
    <div @click="append(0)" class="button , zero"> 0 </div>
    <div @click="dot" class="button"> . </div>
    <div @click="equal" class="button operator"> = </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      previous: null,
      operatorClicked: false,
      current: '',
      operator: null
    }
  },
  methods: {
    clear() {
      this.current = '';
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ? 
        this.current.slice(1) : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current)/ 100}`;
    },
    append(number) {
      if(this.operatorClicked) {
      this.current = '';
      this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      if(this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (a,b) => a / b;
      this.setPrevious();

    },
    times() {
      this.operator = (a,b) => a * b;
      this.setPrevious();
    },
    minus() {
      this.operator = (a,b) => a - b;
      this.setPrevious();
    
    },
    add() {
      this.operator = (a,b) => a + b;
      this.setPrevious(); 
    },
    equal() {
      
    }
  }
};
</script>

<style scoped>
.calculator {
  width:400px;
  font-size: 20pt;
  display: grid;
  grid-template-columns: repeat(4, 1fr); 
  grid-auto-rows: minmax(50px, auto); 
}
.display {
  grid-column: 1 / 5;
  background-color:black;
  color: white;
  text-align: center;
  border-radius:5pt;
}
.zero {
  grid-column: 1 / 3;
}
.button {
  background-color:#F2F2F2;
  border: 1px solid lightgrey;
  border-radius:5pt;
  text-align: center;
}
.operator {
  background-color:orange;
  color: white;
}
</style>
