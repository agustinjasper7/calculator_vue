<script setup>
import { reactive } from "vue"
import NumberButton from "./components/NumberButton.vue"
import OperationButton from "./components/OperationButton.vue";
import EqualButton from "./components/EqualButton.vue";

const app_state = reactive({
  display: "0",
  operation: null,
  store: null,
})

function updateDisplay(number) {
  app_state.display = number;
}

function reset() {
  app_state.display = "0";
  app_state.store = null;
  app_state.operation = null;
}

function storeOperation(operation, number=null) {
  app_state.operation = operation;
  if(number!==null){
    app_state.store = number;
  }
  app_state.display = "0"
}
</script>

<template>
  <header>
    <div>
      <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
      <h1>Calculator</h1>
      <h3>A simple calculator app using Vue JS</h3>
    </div>
  </header>
  <main>
    <div class="calculator">
      <div class="answer">{{ app_state.display }}</div>
      <div class="buttons">
        <NumberButton :number="7" :state="app_state" @number="updateDisplay" />
        <NumberButton :number="8" :state="app_state" @number="updateDisplay" />
        <NumberButton :number="9" :state="app_state" @number="updateDisplay" />
        <OperationButton :operation="'/'" :state="app_state" @operation="storeOperation" />
        <NumberButton :number="4" :state="app_state" @number="updateDisplay" />
        <NumberButton :number="5" :state="app_state" @number="updateDisplay" />
        <NumberButton :number="6" :state="app_state" @number="updateDisplay" />
        <OperationButton :operation="'*'" :state="app_state" @operation="storeOperation" />
        <NumberButton :number="1" :state="app_state" @number="updateDisplay" />
        <NumberButton :number="2" :state="app_state" @number="updateDisplay" />
        <NumberButton :number="3" :state="app_state" @number="updateDisplay" />
        <OperationButton :operation="'-'" :state="app_state" @operation="storeOperation" />
        <NumberButton :number="0" :state="app_state" @number="updateDisplay" />
        <button id="clear" @click="reset">C</button>
        <EqualButton :state="app_state" @number="updateDisplay" @operation="storeOperation" />
        <OperationButton :operation="'+'" :state="app_state" @operation="storeOperation" />
      </div>
    </div>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.calculator {
  border: solid thin #fff;
  padding: 10px;
  margin: 0;
  position: relative;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  background-color: #AAA;
  border-radius: 2.5%;
}

div.answer {
  font-size: 2.5rem;
  text-align: right;
  color: #000;
  padding: 5px;
  background-color: #fff;
  border: solid #000 thin;
}

div.buttons{
  padding: 5px 0 0 0;
}

button {
  font-size: 1.5rem;
  width: 25%;
  border-radius: 10%;
}

button#clear {
  background-color: #FF0;
}

.logo {
  margin: 0;
}
</style>
