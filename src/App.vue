<script setup>
import {ref, shallowRef} from 'vue';
import Fruits from './components/Fruits.vue';
import Post from './components/Post.vue';
import ComponentA from './components/ComponentA.vue';
import ComponentB from './components/ComponentB.vue';

const activeComponent = shallowRef(ComponentA)

function setAActive(){
    activeComponent.value = ComponentA;
}

function setBActive(){
    activeComponent.value = ComponentB;
}
</script>

<template>
  <p>
    <Component :is="activeComponent"/>
  </p>

  <button @click="setAActive()" class="mt-5 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
    Show A
  </button>
  <button @click="setBActive()" class="ml-5 mt-5 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
    Show B
  </button>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
