<template>
  <div @wheel="scrollCounter" class="flex justify-between">
    <CrementerCounterDecrementer/>
    <CrementerCounterDisplay/>
    <CrementerCounterIncrementer/>
  </div>
</template>

<script setup>
import { useCounterStore } from '~~/store';
const counterStore = useCounterStore();

function scrollCounter (e) {  
  if (e.deltaY < 0) {
    counterStore.$patch({
      counter: counterStore.counter + 1
    })
  }

  if (e.deltaY > 0 && counterStore.counter > 0) {
    counterStore.$patch({
      counter: counterStore.counter - 1
    })
  }
}
</script>