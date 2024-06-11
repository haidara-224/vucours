<template>
    <div>
        <input type="number" name="" v-model="x" id="" class="border rounded-3 outline-none p-1 m-1">
        <input type="number" name="" v-model="y" id="" class="border rounded-3 outline-none p-1 m-2">
      <select name="" id="" class="border w-full p-2 outline-none" v-model="operator">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="x">x</option>
        <option value="/">/</option>
      </select>
        <p> {{ Result }}</p> 
    </div>
</template>
<script setup>
import { computed, ref } from 'vue';

const x=ref(0)
const y=ref(0)
const operator=ref('+')

const Result=computed(()=>{
    switch(operator.value){
        case '+':
            return x.value +y.value
        case '-':
            return x.value - y.value
        case 'x':
            return x.value * y.value    
        case '/':
            return x.value / y.value
    }
})

</script>