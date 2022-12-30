<script setup>
let result = " ";
function clear(){
 result = " ";
 function dot(){
  if (result.indexOf(",") === -1){

  }
 }
 let a = "a";
function dollar(){
  this.result = `${a}$`;
}
</script>

<template>
  <div id="calculator">
    <div id="screen">{{ result || "0" }}</div>
    <div id="function_buttons">
      <button @click="clear" >CE</button>
      <button>,</button>
      <button @click="dollar()">$</button>
      <button>€</button>
      <button>¥</button>
      <button>=</button>
    </div>
    <div id="operator_buttons">
      <div id="number_buttons">
        <button id="7">7</button>
        <button id="8">8</button>
        <button id="9">9</button>
        <button id="4">4</button>
        <button id="5">5</button>
        <button id="6">6</button>
        <button id="1">1</button>
        <button id="2">2</button>
        <button id="3">3</button>
        <button id="zero">0</button>
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
