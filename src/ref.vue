<template>
    <div>
        <input type="number" v-model="a" name="" id="" class="border rounded-full outline-none p-3">
        <input type="number" v-model="b" name="" id="" class="border rounded-full outline-none p-3">
        <input type="text" v-model="calcul" name="" id="" class="border rounded-full outline-none p-3" disabled>
    </div>
</template>
<script setup>
import { ref, watch } from 'vue';

let a=ref(0)
let b=ref(0)
let calcul=ref(0)

function updateCalcul()
{
    calcul.value=a.value+b.value
}
watch([a, b], updateCalcul);

</script>