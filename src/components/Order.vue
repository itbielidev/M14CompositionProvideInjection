<script setup lang="ts">
    import { inject } from 'vue';
    import type { Ingredient } from '@/types/ingredient';

    const products = inject<Ingredient[]>('order')
    const currency = inject('coin')
</script>
<template>
<div class="foodItem">
    <div
      class="item"
      v-for="ingredient in products"
      :key="ingredient.name">
      <p class="ingredient">{{ ingredient.name }}</p>
      <p class="ingredientPrice">{{ currency }} {{ingredient.price.toFixed(2) }}</p>
    </div>
    <hr>
      <strong>Total:{{ currency }} {{ products?.reduce((acc, cur) => cur.price + acc,0) }}</strong>
</div>
</template>

<style scoped>
div.foodItem{
    display: flex;
    justify-content: center;
    flex-direction: column;
}
</style>