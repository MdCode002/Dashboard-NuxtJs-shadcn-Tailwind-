<template>
  <div>
    <header class="flex items-center gap-2 p-4 hover:scale-[101%] transition cursor-pointer">
      <Logo />
    </header>
    <div class="px-4 grow">
      <div class="grid gap-2">
        <NuxtLink :href="item.path" v-for='(item, index) in items' :key='index'
          class="flex items-center gap-2 px-2 py-1 transition rounded cursor-pointer hover:bg-neutral-100">
          <Icon size="20" :name="item.icon" color="black" />
          <span>{{ item.title }}</span>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup>

const items = ref([
  { title: "Overview", path: "/" ,icon:"ri:dashboard-line"},
  { title: "Transactions", path: "/transactions" ,icon:"uil:transaction"},
  { title: "Account", path: "/account",icon:"mdi:account" },
  { title: "Contacts", path: "/contacts",icon:"material-symbols:contacts" },
  { title: "Settings", path: "/settings" ,icon:"material-symbols:settings"},
]);
</script>
