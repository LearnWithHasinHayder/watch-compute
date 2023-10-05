<script setup>
import { ref, computed } from 'vue';
const fruitsWithPrice = ref([
    { name: 'Apple', price: 1.20 },
    { name: 'Orange', price: 1.40 },
    { name: 'Banana', price: 1.60 },
    { name: 'Mango', price: 1.80 },
    { name: 'Pineapple', price: 2.10 },
]);


const totalPrice = computed(()=>{
    console.log("Computed")
    let total = 0;
    for(let i = 0; i < fruitsWithPrice.value.length; i++){
        total += fruitsWithPrice.value[i].price*1;
    }
    return total.toFixed(2);
})

const totalPrice2 = function(){
    console.log("Function")
    let total = 0;
    for(let i = 0; i < fruitsWithPrice.value.length; i++){
        total += fruitsWithPrice.value[i].price*1;
    }
    return total.toFixed(2);
}


</script>
 
<template>

    <p> C Total: {{ totalPrice }}  </p>
    <p> C Total: {{ totalPrice }}  </p>
    <p> C Total: {{ totalPrice }}  </p>
    <p> D Total: {{ totalPrice2() }}  </p>
    <p> D Total: {{ totalPrice2() }}  </p>
    <p> D Total: {{ totalPrice2() }}  </p>

</template>
 
<style scoped></style>