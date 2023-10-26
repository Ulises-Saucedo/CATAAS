<template>
  <header class="h-[75px] bg-slate-700 text-white flex items-center justify-center">
    <h1 class="text-4xl">CATAAS</h1>
  </header>
  <section class="p-4 grid grid-cols-5 gap-4">
    <div v-for="element in data" class="inline-block pb-4 border-2">
      <img :src="'https://cataas.com/cat/' + element._id" class="h-[200px] w-full">
      <p v-for="e in element.tags" class="inline m-4">
        {{ e }}
      </p>
    </div>
  </section>
</template>

<script>
  export default {
    name: 'App',
    data (){
      return {
        data: null
      }
    },
    created(){
      fetch('https://cataas.com/api/cats?tags=cute')
        .then(response => response.json())
        .then(dataJson => this.data = dataJson)
    }
  }
</script>