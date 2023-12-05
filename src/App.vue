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

function showAlert(){
  if (orderTitle.value!==''){
  alert("Your order has been placed")
  }
}

function currencyChanged(e:Event){
  console.log((e.target as HTMLSelectElement).value)
}

</script>

<template>
  <h1>{{ orderTitle }}</h1>
  <form action="/" method="get">
    <input v-model="orderTitle" name="clientName" class="clientName" type="text" />
  <button class="sendOrder" @click="() => showAlert()">Place Order</button>
  </form>
  <div class="ticket">
    <div>
    <label for="currency">Currency</label>
    <select name="currency" class="currency" @input="currencyChanged">
        <option value="dolars">Dollars($)</option>
        <option value="euros">Euros(€)</option>
      </select>
 </div>
    <div
      class="item"
      v-for="ingredient in ingredientChoice"
      :key="ingredient.name">
      <p class="ingredient">{{ ingredient.name }}</p>
      <Currency></Currency>
      <p class="ingredientPrice">{{ingredient.price.toFixed(2) }}</p>
      <button>Add to Cart</button>
    </div>
  </div>
</template>

<style>
.currency{
  text-align: center;
  width: auto;
  background-color: white;
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
