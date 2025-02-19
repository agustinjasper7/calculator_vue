<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
    number: {
        "type": Number,
        "required": true,
    },
    state: {
        "type": Object,
        "required": true
    }
})

const emit = defineEmits(["number"])

function display(){
    if(props.state.display === "0"){
        emit("number", "")
    }
    emit("number", props.state.display + props.number);
}
</script>

<template>
    <button @click="display">{{ props.number }}</button>
</template>

<style scoped>
button {
    background-color: #BBF;
}
</style>