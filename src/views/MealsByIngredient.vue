<template>
    <div class="p-8 pb-0">
        <h1 class="text-4xl font-bold mb-4 text-orange-500">Ingredientes para {{ ingredient }}</h1>
    </div>
    <Meals :meals="meals" />
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import Meals from '../components/Meals.vue';


const route = useRoute();
const meals = computed(() => store.state.mealsByIngredient)
const ingredient = computed(() => route.params.ingredient)


onMounted(() => {
    store.dispatch('searchMealsByIngredient', route.params.ingredient);
})
</script>