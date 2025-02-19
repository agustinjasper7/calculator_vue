<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
    state: {
        "type": Object,
        "required": true
    }
})

const emit = defineEmits(["number", "operation"])

function calculate(){
    var temp = Number(props.state.display)
    var answer = 0
    if(props.state.operation === '+') answer = props.state.store + temp;
    else if(props.state.operation === '-') answer = props.state.store - temp;
    else if(props.state.operation === '*') answer = props.state.store * temp;
    else if(props.state.operation === '/') answer = Math.floor(props.state.store / temp);
    else answer = props.state.store % temp;
    emit("operation", null);
    emit("number", String(answer));
}
</script>

<template>
    <button @click="calculate" :disabled="!props.state.operation">=</button>
</template>

<style scoped>
button {
    background-color: #FF0;
}
button:disabled {
    background-color: #AA0;
}
</style>