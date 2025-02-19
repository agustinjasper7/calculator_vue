<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
    operation: {
        "type": String,
        "required": true,
    },
    state: {
        "type": Object,
        "required": true
    }
})

const emit = defineEmits(["operation"])

function operate(){
    if(!props.state.operation){
        emit("operation", props.operation, Number(props.state.display));
        return;
    }
    emit("operation", props.operation)
}
</script>

<template>
    <button @click="operate" :class="{ selected: props.state.operation == props.operation }">{{ props.operation }}</button>
</template>

<style scoped>
button {
    background-color: #B33;
}

button.selected {
    background-color: #F00;
}
</style>