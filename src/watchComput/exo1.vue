<template>
    <div>
        <input type="text" name="" v-model="nom" id="" class="border rounded-3 outline-none p-1 m-1">
        <input type="text" name="" v-model="prenom" id="" class="border rounded-3 outline-none p-1 m-2">
        <p>{{ fullname }}</p>
        
    </div>
</template>
<script setup>
import {computed, ref, watch} from 'vue'
const nom=ref('')
const prenom=ref('')
const fullname=computed(()=>{
    return `votre nom et prenom est:  ${nom.value} ${prenom.value}`
})
watch(prenom,(newValue,oldValue)=>{
    console.log(`votre nouveau nom est ${oldValue}`)
})

</script>