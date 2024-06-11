<template>
    <div>
        <input type="color" name="" v-model="color" id="" class="border rounded-3 outline-none p-1 m-1">
        <input type="text" name="" v-model="taille" id="" class="border rounded-3 outline-none p-1 m-2">
        <p :style="TextStyle">Bonjour sidy</p>
    </div>
</template>
<script setup>
import { computed, ref, watch } from 'vue';

const color=ref('black')
const taille=ref(12)
const TextStyle=computed(()=>({
    color: color.value,
    fontSize: taille.value +'px',
}))
watch(color,(newValue,oldValue)=>{
    console.log(`ancienne couleur ${oldValue}, nouvelle Couleur ${newValue}`)
})
watch(taille,(newValue,oldValue)=>{
    console.log(`ancienne taille ${oldValue}, nouvelle Taille ${newValue}`)
})
</script>
