<script setup>
import { ref } from "vue";

let result = ref("8");
let operator;
let resultPrevius;
function clear() {
  result = " ";
}
function dot() {
  if (this.result.indexOf(",") === -1) {
  }
}
function dollar() {
  if (this.result.indexOf("$") === -1) {
    this.result = `${this.result}$`;
  }
}
function euro() {
  if (this.result.indexOf("€") === -1) {
    this.result = `${this.result}€`;
  }
}
function yen() {
  if (this.result.indexOf("¥") === -1) {
    this.result = `${this.result}¥`;
  }
}

function equal(){
  this.result = `${this.operator(parseFloat(this.result),parseFloat(this.resultPrevius))}` ; this.resultPrevius = null;
}

function number(number){
  this.result = `${this.result}${number}`
}

function sum(){

}
</script>

<template>
  <div id="calculator">
    <div id="screen">{{ result || "0" }}</div>
    <div id="function_buttons">
      <button @click="clear()">CE</button>
      <button>,</button>
      <button @click="dollar()">$</button>
      <button @click="euro()">€</button>
      <button @click="yen()">¥</button>
      <button>=</button>
    </div>
    <div id="operator_buttons">
      <div id="number_buttons">
        <button @click="number('7')" id="7">7</button>
        <button @click="number('8')" id="8">8</button>
        <button @click="number('9')" id="9">9</button>
        <button @click="number('4')" id="4">4</button>
        <button @click="number('5')" id="5">5</button>
        <button @click="number('6')" id="6">6</button>
        <button @click="number('1')" id="1">1</button>
        <button @click="number('2')" id="2">2</button>
        <button @click="number('3')" id="3">3</button>
        <button @click="number('0')" id="zero">0</button>
      </div>
      <div id="action_buttons">
        <button>+</button>
        <button>-</button>
        <button>x</button>
        <button>÷</button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../sass/mixin.scss";
@import "../sass/variables";
@import "../sass/action_buttons.scss";
@import "../sass/number_buttons.scss";
@import "../sass/function_buttons.scss";
@import "../sass/screen.scss";
#operator_buttons {
  display: flex;
}
</style>
