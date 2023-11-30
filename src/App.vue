<script setup >
import Order from '@/components/Order.vue'
import Currency from '@/components/Currency.vue'
const ingredientChoice = [    
     { name: "Hamburger 🍔.", price: 5 },
     { name: "Cheeseburger 🧀", price: 6 },
     { name: "Impossible Burger 🥕", price: 7 },
     { name: "Fries 🍟", price: 2 }];
</script>

<template>
<h1>The Snazzy Burger</h1>
<input class="clientName" type="text">
<button class="sendOrder">Place Order</button>
<div class="ticket">
<div class="item" v-for="(name, price) in ingredientChoice"/>
<p class="ingredient">{{ingredientChoice.name}}</p>
    <p class="ingredientPrice">{{ ingredient.price }}</p>
    <button class="">Add to Cart</button>
</div>
</div>
</template>

<style >
#app{
  display: flex;
  flex-direction: column;
  width: 40rem;
  justify-content: center;

}
h1{
 align-self: center;
 margin-bottom: 10px;
 width: 10rem;
 text-align: center;
 
}

.clientName{
  align-self: center;
  width: 20rem;
  margin-bottom: 5px;
}

.sendOrder{
  align-self: center;
  width: auto;
}
</style>