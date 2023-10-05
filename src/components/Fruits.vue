<script setup>
import { ref, computed } from 'vue';
const fruitsWithPrice = [
    { name: 'Apple', price: 1.20 },
    { name: 'Orange', price: 1.40 },
    { name: 'Banana', price: 1.60 },
    { name: 'Mango', price: 1.80 },
    { name: 'Pineapple', price: 2.10 },
];



const index = ref(0);
// const currentFruit = ref(fruitsWithPrice[index.value]);

const currentFruit = computed(() => fruitsWithPrice[index.value]);
// const currentFruit = computed(() => {
//     return fruitsWithPrice[index.value]
// });


const next = () => {
    index.value = (index.value + 1) % fruitsWithPrice.length;
};
</script>
 
<template>

    <p class="mb-2">
        Index: {{ index }}
    </p>
    <p class="mb-2">
        Fruit: {{ currentFruit.name }}
    </p>
    <p class="mb-2">
        Price: {{ currentFruit.price }}
    </p>
    <p class="mt-5">
        <button @click="next()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
            Next Fruit
        </button>
    </p>
</template>
 
<style scoped></style>