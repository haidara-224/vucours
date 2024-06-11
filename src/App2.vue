<template>
<div>
    <h1 style="color: red;">Bonjour le monde {{ name }}</h1>
</div>
    
</template>
<script setup>
import { ref } from 'vue';

const name=ref('sidy')

const reverse=name.value.split().reverse().join('')
console.log(reverse)
</script>