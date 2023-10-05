<script setup>
import { ref, reactive, watch, watchEffect } from 'vue';
const postId = ref(1);
const post = reactive({
    title: '',
})

watchEffect(async () => {
    post.title = "Loading...";
    const response = await fetch(`https://jsonplaceholder.typicode.com/posts/${postId.value}`);
    const json = await response.json();
    post.title = json.title;
})


//async watch
// watch(postId, async (newVal, oldVal)=>{
//     post.title = "Loading...";
//     const response = await fetch(`https://jsonplaceholder.typicode.com/posts/${newVal}`);
//     const json = await response.json();
//     post.title = json.title;
// },{immediate: true})

// watch(postId, (newVal, oldVal)=>{
//     post.title = "Loading...";
//     fetch(`https://jsonplaceholder.typicode.com/posts/${newVal}`)
//     .then(response => response.json())
//     .then(json => {
//         post.title = json.title;
//     })
// },{immediate: true})
</script>
 
<template>
    <p>
        Post ID: {{ postId }}
    </p>
    <p>
        Post Title: {{ post.title }}
    </p>
    <p class="mt-10">
        <input type="text" v-model="postId">
    </p>
</template>
 
<style scoped></style>