<template>
    <div class="pagination">
        <div class="data">
            <!-- Afficher les données de la page courante -->
            <ul>
                <li v-for="item in currentPageData" :key="item.id">{{ item.name }}</li>
            </ul>
        </div>
        <div class="controls">
            <!-- Boutons de pagination -->
            <button @click="prevPage" :disabled="currentPage === 1">Previous</button>
            <span>{{ currentPage }}</span>
            <button @click="nextPage" :disabled="currentPage === totalPages">Next</button>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';

// Données à paginer
const items = ref([
    { id: 1, name: 'Item 1' },
    { id: 2, name: 'Item 2' },
    { id: 3, name: 'Item 3' },
    { id: 4, name: 'Item 4' },
    { id: 5, name: 'Item 5' },
    { id: 6, name: 'Item 6' },
   
    // Ajouter d'autres éléments
]);

// Nombre d'éléments par page
const itemsPerPage = 2;

// Page actuelle
const currentPage = ref(1);

// Calcul du nombre total de pages
const totalPages = computed(() => Math.ceil(items.value.length / itemsPerPage));

// Données de la page courante
const currentPageData = computed(() => {
    const start = (currentPage.value - 1) * itemsPerPage;
    const end = start + itemsPerPage;
    return items.value.slice(start, end);
});

// Fonction pour passer à la page précédente
const prevPage = () => {
    if (currentPage.value > 1) {
        currentPage.value--;
    }
};

// Fonction pour passer à la page suivante
const nextPage = () => {
    if (currentPage.value < totalPages.value) {
        currentPage.value++;
    }
};
</script>

<style>
.pagination {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.controls {
    margin-top: 10px;
}

.controls button {
    margin: 0 5px;
}
</style>
