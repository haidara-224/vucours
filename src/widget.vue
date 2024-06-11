<template>
    <div class="flex flex-row-reverse gap-7">
        <div class="border ronded w-[200px] h-[200px]" :style="{ backgroundColor:color,borderRadius: rounded + 'px',borderRadius: rounded + 'px', boxShadow: boxShadowValue}">

        </div>
        <div class="flex flex-col gap-y-4">
            <span>color</span><input type="color" v-model="color">
            
            <span>rounded</span><input type="range" name="" id="" min="3" max="50" v-model="rounded">
            <span>Shadow</span><input type="range" name="" id="" v-model="shadowDepth">


        </div>
    </div>
</template>
<script setup>
import {ref,watch} from 'vue'
const color = ref('#ffffff')
const rounded=ref(0)
const shadowDepth = ref(0);
const boxShadowValue = ref('');
watch(shadowDepth, (newValue) => {
  const shadow = `${newValue}px ${newValue}px ${newValue * 2}px rgba(0, 0, 0, 0.2)`;
  boxShadowValue.value = shadow;
});


</script>
