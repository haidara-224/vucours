<template>
    <div class="flex justify-center items-center flex-col">

      <div class="border rounded w-full h-4 my-6 bg-gray-200">
        <div :style="{ width: progresse + '%', transition: 'width 0.3s ease' }" class="h-full bg-green-500 rounded-md flex justify-center items-center"><span class="text-center text-white">{{ progresse }} %</span></div>
      </div>
      

      <div>
      <p>Nombre de Tache completer: {{ completedTache }}</p>

        <input type="text" v-model="recher" name="" id="" class="border outline-none" placeholder="Rechercher">
      </div>
      

      <ul class="border rounded w-[400px] flex justify-center items-center flex-col my-1 py-5">
        <li v-for="Anim in filteredAnimaux" :key="Anim.id" class="p-3 space-x-16 border w-full" :class="Anim.completed ? 'line-through text-pink-200' : ''">
          {{ Anim.name }}
          <button @click.prevent="deleteTodo(Anim.id)" class="border bg-red-600 h-auto text-white px-5 float-right">x</button>
          <input type="checkbox" v-model="Anim.completed" @change="updateProgressBar">
        </li>
      </ul>
      
     
      <div>
        <input v-model="items" type="text" name="" id="" class="border outline-none" placeholder="Entrer un animal">
        <button class="border bg-green-950 text-white h-auto px-4" @click.prevent="AddTodo">v</button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed, watch, nextTick } from 'vue';
  
  const Animaux = ref([
    { id: 1, name: 'chien', completed: true },
    { id: 2, name: 'chat', completed: true },
    { id: 3, name: 'souris', completed: false },
    { id: 4, name: 'mouton', completed: false }
  ]);
  
  const items = ref('');
  const recher = ref('');
  let progresse = ref(0);
  

  const AddTodo = () => {
    if (items.value.trim() !== '') {
      Animaux.value.push({ id: Date.now(), name: items.value, completed: false });
      items.value = '';
      updateProgressBar();  
    } else {
      alert('Veuillez entrer une valeur');
    }
  };
  

  const deleteTodo = (id) => {
    Animaux.value = Animaux.value.filter((animaux) => animaux.id !== id);
    updateProgressBar(); 
  };
  
  
  const filteredAnimaux = computed(() => {
    return Animaux.value.filter(anim => 
      anim.name.toLowerCase().includes(recher.value.toLowerCase())
    );
  });
  

  const updateProgressBar = () => {
    const total = Animaux.value.length;
    const completed = Animaux.value.filter(anim => anim.completed).length;
    progresse.value = total > 0 ? (completed / total) * 100 : 0;
  };
  const completedTache=computed(()=>{
    return Animaux.value.filter(anim=>anim.completed).length
  })
  let previousAnimauxState = JSON.parse(JSON.stringify(Animaux.value));
watch(Animaux, (newAnim, oldAnim) => {
  newAnim.forEach((animal, index) => {
    if (animal.completed !== previousAnimauxState[index]?.completed) {
      console.log(`La tâche "${animal.name}" est ${animal.completed ? 'complétée' : 'non complétée'}`);
    }
  });
  nextTick(() => {
    previousAnimauxState = JSON.parse(JSON.stringify(newAnim));
  });
}, { deep: true });


  watch(Animaux, updateProgressBar, { deep: true });
  

  updateProgressBar();
  </script>
  