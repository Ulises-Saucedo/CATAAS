<template>
  <header class="h-[75px] bg-slate-700 text-white flex items-center justify-center">
    <h1 class="text-4xl">CATAAS</h1>
  </header>
  <section class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 grid-rows-[200px, auto] gap-4 mt-5 mb-5 container m-auto">
    <div v-for="element in data" class="inline-block pb-4 shadow-md">
      <img :src="'https://cataas.com/cat/' + element._id" class="h-[200px] w-full">
      <p v-for="e in element.tags" class="inline-block m-2 rounded bg-indigo-400 bg-opacity-10 p-2">
        {{ e }}
      </p>
    </div>
  </section>
</template>

<script setup>
  import { onMounted, ref } from 'vue';
  let data = ref([])

  onMounted(() =>{
    fetch('https://cataas.com/api/cats?tags=cute')
      .then(response => response.json())
      .then(dataJson => data.value = dataJson)
  })
</script>