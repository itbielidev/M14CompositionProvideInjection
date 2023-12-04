<script setup lang="ts">
import Order from "@/components/Order.vue";
import Currency from "@/components/Currency.vue";
import { ref } from "vue";

const ingredientChoice = [
  { name: "Hamburger 🍔.", price: 5 },
  { name: "Cheeseburger 🧀", price: 6 },
  { name: "Impossible Burger 🥕", price: 7 },
  { name: "Fries 🍟", price: 2 },
];

const orderTitle = ref("");

</script>

<template>
  <h1>{{ orderTitle }}</h1>
  <form action="/" method="get">
    <input v-model="orderTitle" name="clientName" class="clientName" type="text" />
  <button class="sendOrder">Place Order</button>
  </form>
  <div class="ticket">
    <div
      class="item"
      v-for="ingredient in ingredientChoice"
      :key="ingredient.name">
      <p class="ingredient">{{ ingredient.name }}</p>
      <p class="ingredientPrice">{{ ingredient.price }}</p>
      <button @click="() => orderTitle = 'askjdasdh'">Add to Cart</button>
    </div>
  </div>
</template>

<style>
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
h1 {
  align-self: center;
  margin-bottom: 10px;
  width: 10rem;
  text-align: center;
}

.clientName {
  align-self: center;
  width: 20rem;
  margin-bottom: 5px;
}

.sendOrder {
  align-self: center;
  width: auto;
}

.ticket {
  margin-top: 5px;
  display: flex;
  flex-direction: column;
}

.item {
  margin-top: 5px;
  display: flex;
  flex-direction: row;
  gap: 10px;
}
</style>
