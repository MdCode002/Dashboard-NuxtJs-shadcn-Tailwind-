<script setup>
const loading = ref(false)
</script>

<template>
  <div class="grid  gap-8">
    <header class="flex item-start justify-between">
      <div>
        <p>Hi Mouhamed welcome back</p>
        <h1>Dashboard</h1>
       </div>
        <div class="bg-neutral-200 w-[80px] h-[30px]">
                
        </div>
     
    </header>
    <main class="grid gap-4">
      <div class=" flex items-center gap-2" >
        <div class="bg-neutral-200 w-[80px] h-[30px]"></div>
        <div class="bg-neutral-200 w-[80px] h-[30px]"></div>
        <div class="bg-neutral-200 w-[80px] h-[30px]"></div>
      </div>
      <section>
        <div class="bg-neutral-200 w-full h-[300px]"></div>    
      </section>
    </main>
    <footer>
      <div class="flex items-center gap-2" >
        <div class="bg-neutral-200 h-[200px] w-full"></div>
        <div class="bg-neutral-200 h-[200px]  w-full "></div>
        <div class="bg-neutral-200 h-[200px]  w-full "></div>
      </div>
    </footer>
  </div>
</template>