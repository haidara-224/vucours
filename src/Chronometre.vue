<template>
    <div class="flex items-center justify-center bg-green-700 w-full h-[300px] rounded-lg text-white flex-col">

        <div>
            <span class="mx-3">{{ formatTime(h) }} h</span>
            <span class="mx-3">{{ formatTime(min) }} min</span>
            <span class="mx-3">{{ formatTime(s) }} s</span>
            <span class="mx-3">{{ formatTime(ms) }} ms</span>

        </div>
        <div>
            <button @click="start" class="mx-3 border p-1 rounded-md w-24 bg-amber-600">sart</button>
            <button @click="stoped" class="mx-3 border p-1 rounded-md w-24 bg-amber-600">stop</button>
            <button @click="renin" class="mx-3 border p-1 rounded-md w-24 bg-amber-600">reinitialiser</button>
        </div>

    </div>
</template>
<script setup>
import { ref } from 'vue';

let h=ref(0)
let min=ref(0)
let s=ref(0)
let ms=ref(0)
let t=ref(0)
function chronometre()
{
    ms.value=ms.value+1
    if(ms.value===90){
        s.value=s.value+1
        ms.value=0
    }
    if(s.value===60){
        min.value=min.value+1
        s.value=0
    }
    if(min.value===60){
        h.value=h.value+1
        m.value=0
    }
    
}
function formatTime(time) {
    return time < 10 ? '0' + time : time;
}
function start(){
    t.value=setInterval(() => {
        chronometre()
    }, 10);

}
function stoped(){
clearInterval(t.value)
}
function renin()
{
 s.value=0
 min.value=0
 ms.value=0
 h.value=0
 clearInterval(t.value)
 
}


</script>