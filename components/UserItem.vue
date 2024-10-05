<script setup>
const loading = ref(false);
const name = ref("Mouhamed Diouf");
const description = ref("CEO of mdsoft");
</script>
<template>
  <div
    class="flex items-center justify-start gap-2 p-2 m-2 border rounded cursor-pointer hover:bg-neutral-100 transition"
    tra
  >
    <div
      class="flex items-center justify-center w-10 h-10 font-bold text-white bg-[#000b26] rounded-full"
    >
      {{ name[0] }}
    </div>
    <div>
      <p class="m-0 text-sm font-bold text-black leading-1">{{ name }}</p>
      <p class="m-0 text-xs">{{ description }}</p>
    </div>
  </div>
</template>
