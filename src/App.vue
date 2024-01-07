<template>
  <header class="h-[75px] bg-slate-700 text-white flex items-center justify-center">
    <h1 class="text-4xl">CATAAS</h1>
  </header>
  <section class="grid grid-cols-1 p-2 sm:grid-cols-2 lg:grid-cols-4 grid-rows-[200px, auto] gap-4 mt-5 mb-5 container m-auto">
    <div v-for="element in data" class="inline-block pb-4 shadow-md rounded overflow-hidden">
      <img :src="'https://cataas.com/cat/' + element._id" class="h-[200px] w-full">
      <div v-for="(e, i) in element.tags" class="inline">
        <button v-if="i < 3" class="m-2 font-semibold rounded shadow bg-indigo-400 bg-opacity-10 p-2 cursor-default bg-gradient-to-r from-indigo-200 via-red-200 to-yellow-100">{{ e }}</button>
      </div>
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