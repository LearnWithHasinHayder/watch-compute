<script setup>
import { ref, watch } from 'vue';
const postId = ref(1);

const fruitsWithPrice = ref([
    { name: 'Apple', price: 1.20 },
    { name: 'Orange', price: 1.40 },
    { name: 'Banana', price: 1.60 },
    { name: 'Mango', price: 1.80 },
    { name: 'Pineapple', price: 2.10 },
]);

const totalPrice = ref(0)
watch(fruitsWithPrice,(newVal, oldVal) => {
    let total = 0;
    for (let i = 0; i < newVal.length; i++) {
        total += newVal[i].price * 1;
    }
    console.log(total);
    totalPrice.value = total.toFixed(2);
}, {deep:true, immediate:true});

const data = ref("Post Id is " + postId.value);

watch(postId, (newVal, oldVal)=>{
    data.value = "Post Id is " + newVal;
})
</script>
 
<template>
    <p> {{ fruitsWithPrice }}</p>
    <p> {{ totalPrice }} </p>
    <p>{{ data }}</p>
<p> 
    Post ID: {{ postId }}
</p>
<p>
    <input type="text" v-model="postId">
</p>
<p>
    <button @click="fruitsWithPrice.pop()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
      Button
    </button>
</p>
</template>
 
<style scoped>
 
</style>