<template>
    <div class="flex justify-center items-center flex-col">
      <button @click.prevent="affiche" class="border w-full rounded">Afficher Tout</button>
      <select name="" id="" class="border rounded-sm w-full" v-model="selected">
        <option v-for="category in categorie" :key="category" :value="category">{{ category}}</option>
      </select>
      <ul class="border rounded w-[400px] flex justify-center items-center flex-col my-1 py-5">
        <li v-for="Produit in selection" :key="Produit.id" class="p-3 space-x-16 border w-full flex justify-between" >
          <div>
          {{ Produit.name }}

          </div>
          <div>
          {{ Produit.category }}

          </div>
        </li>
      </ul>
     {{ selected }}
    </div>
  </template>
  
  <script setup>
  import { computed, ref, } from 'vue';
  
  const Produits = ref([
    { id: 1, name: 'Iphone', category: 'telephone' },
    { id: 2, name: 'samsungs24', category: 'telephone' },
    { id: 3, name: 'Lenovo', category: 'ordinateur' },
    { id: 4, name: 'Hp', category: 'ordinateur' }
  ]);
  const categorie=ref(['telephone', 'ordinateur'])
  const selected=ref('')
  const selection = computed(() => {
  return selected.value
    ? Produits.value.filter((Product) => Product.category === selected.value)
    : Produits.value;
});
const affiche=(()=>{
  selected.value=''
})
  


 
  </script>
  