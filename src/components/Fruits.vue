<script setup>
import { ref, computed } from 'vue';
const fruitsWithPrice = ref([
    { name: 'Apple', price: 1.20 },
    { name: 'Orange', price: 1.40 },
    { name: 'Banana', price: 1.60 },
    { name: 'Mango', price: 1.80 },
    { name: 'Pineapple', price: 2.10 },
]);

const fruitName = ref('');
const fruitPrice = ref(0);
const add = ()=>{
    fruitsWithPrice.value.push({
        name: fruitName.value,
        price: fruitPrice.value
    });
    fruitName.value = '';
    fruitPrice.value = 0;
}

const totalPrice = computed(()=>{
    let total = 0;
    for(let i = 0; i < fruitsWithPrice.value.length; i++){
        total += fruitsWithPrice.value[i].price*1;
    }
    return total.toFixed(2);
})

// let totalPrice = ref(0);
// for(let i = 0; i < fruitsWithPrice.value.length; i++){
//     totalPrice.value += fruitsWithPrice.value[i].price;
// }
// totalPrice.value = totalPrice.value.toFixed(2);

</script>
 
<template>
    <p class="mb-10">{{ fruitsWithPrice }}</p>
    <p>Fruit Name: <input  v-model='fruitName'/></p>
    <p>Fruit Price: <input  v-model='fruitPrice'/></p>
    <!-- <p>Fruit Price: <input type="number" v-model='fruitPrice'/></p> -->
    <p> Total: {{ totalPrice }}  </p>
    <p class="mt-5">
        <button @click="add()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
            Add Fruit
        </button>
    </p>
</template>
 
<style scoped></style>