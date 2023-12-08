<script setup lang="ts">
  const {currency} = defineProps(['currency'])
</script>

<template>
 <!-- <div>
    <label for="currency">Currency</label>
    <select name="currency" class="currency">
        <option value="dolars">Dollars($)</option>
        <option value="euros">Euros(€)</option>
      </select>
 </div> -->

<span id="currency">{{ currency }}</span>

</template>

<style scoped >
/* div{
    display: flex;
    justify-content: center;
}
.currency{
  text-align: center;
  width: auto;
  background-color: white;
  border-color: black;
  text-decoration: none;
} */
</style>