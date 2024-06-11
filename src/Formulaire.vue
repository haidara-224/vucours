<template>
    <div class="flex justify-center items-center h-96 flex-col">
      <div>
        <p v-if="Error" class="text-red-700">
            {{ message }}
        </p>
        <p v-else class="text-green-900">
            {{ message }}

        </p>
      </div>
        <form @submit.prevent="onSubmit" class="flex justify-center bg-slate-500 px-[40px] py-[80px] rounded-2xl shadow-slate-950 flex-col items-center w-[34%] ">
            <input v-model="inputUsername" type="text" placeholder="entrer votre nom" class="border my-1 w-full px-5 py-1 rounded-md outline-none">
            <input v-model="inputPassword" type="password" name="" id="" placeholder="Entrer votre PasseWord" class="border my-1 w-full px-5 py-1 rounded-md outline-none">
            <button class="border my-1 w-full px-5 py-1 rounded-md outline-none text-white bg-neutral-900">Enregister</button>

        </form>
     
        
    </div>
</template>
<script setup>
import { ref } from 'vue';

const userName=ref('sidy')
const password=ref('1234')
const inputUsername=ref('')
const inputPassword=ref('')
const Error=ref(false)
const message=ref('')
/**
 * 
 * @param e PointerEvent
 */
const onSubmit=(e)=>{
   
if(inputUsername.value!==userName.value ||inputPassword.value!==password.value)
{
    message.value='Identifiant ou mot de passe invalide'
    Error.value=true
    return
}else{
    message.value='Vous etes bien connecter'
    Error.value=false
}

}

</script>