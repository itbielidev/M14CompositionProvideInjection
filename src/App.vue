<script setup lang="ts">
import { ref, provide } from "vue";

import CalculatePrice from "@/components/CalculatePrice.vue";
import Order from '@/components/Order.vue'
import type {Ingredient} from '@/types/ingredient';

const orderTitle = ref("");
const currency = ref("€");
const cart = ref<Ingredient[]>([])

provide('order', cart)
provide('coin', currency)

const ingredientChoice: Ingredient[] = [
  { name: "Hamburger 🍔.", price: 5 },
  { name: "Cheeseburger 🧀", price: 6 },
  { name: "Impossible Burger 🥕", price: 7 },
  { name: "Fries 🍟", price: 2 },
];

function showAlert(){
  if (orderTitle.value!==''){
    alert("Your order has been placed")
  }
}

function addToCart(ingredient: Ingredient) {
  cart.value.push(ingredient)
}


</script>

<template>
  <h1>{{ orderTitle }}</h1>
  <input v-model="orderTitle" name="clientName" class="clientName" type="text" />
  <button class="sendOrder" @click="() => showAlert()">Place Order</button>
  <div class="ticket">
    <div>
    <label for="currency">Currency</label>
    <select name="currency" class="currency" v-model="currency">
      <option value="$">Dollars($)</option>
      <option value="€">Euros(€)</option>
    </select>
  </div>
    <div
      class="item"
      v-for="ingredient in ingredientChoice"
      :key="ingredient.name">
      <p class="ingredient">{{ ingredient.name }}</p>
      <CalculatePrice :currency="currency" />
      <p class="ingredientPrice">{{ingredient.price.toFixed(2) }}</p>
      <button @click="() => addToCart(ingredient)">Add to Cart</button>
    </div>
  </div>

  <section>
    <h2>Your order</h2>
    <Order />
  </section>
</template>

<style>
.currency{
  text-align: center;
  width: auto;
  border-color: black;
  text-decoration: none;
}

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
