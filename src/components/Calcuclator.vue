<script setup>
import { ref } from "vue";
let previous;
let result = ref("");
let operator;
let operatorClicked = false;

function clear() {
  this.result = "";
}
function dot() {
  if (this.result.indexOf(".") === -1) {
    this.number(".");
  }
}
function dollar() {
  this.result = `${this.result}$`;
}
function euro() {
  this.result = `${this.result}€`;
}
function yen() {
  this.result = `${this.result}¥`;
}
function equal() {
  this.result = `${operator(parseFloat(this.result), parseFloat(previous))}`;
  previous = null;
}

function number(number) {
  if (operatorClicked) {
    this.result = "";

    operatorClicked = false;
  }
  this.result = `${this.result}${number}`;
}

function setPrevious() {
  previous = this.result;
  operatorClicked = true;
}
function sum() {
  operator = (num1, num2) => num1 + num2;
  this.setPrevious();
}
function substract() {
  operator = (num1, num2) => num1 - num2;
  this.setPrevious();
}
function multiplication() {
  operator = (num1, num2) => num1 * num2;
  this.setPrevious();
}
function division() {
  operator = (num1, num2) => num1 / num2;
  this.setPrevious();
}
</script>

<template>
  <div id="calculator">
    <div id="screen">{{ result || "0" }}</div>
    <div id="function_buttons">
      <button @click="clear()">CE</button>
      <button @click="dot()">,</button>
      <button @click="dollar()">$</button>
      <button @click="euro()">€</button>
      <button @click="yen()">¥</button>
      <button @click="equal()">=</button>
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
        <button @click="sum()">+</button>
        <button @click="substract()">-</button>
        <button @click="multiplication()">x</button>
        <button @click="division()">÷</button>
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
