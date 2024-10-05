<template>
  <div>
    <div>
      <div class="z-50 flex item-center justify-between w-full h-full p-4 lg:hidden">
        <Logo />
        <Icon
          class="z-50 cursor-pointer left-2 top-2"
          size="40"
          name="ic:outline-menu"
          color="#000b26"
          @click="open = true"
        />
        <div v-if="open" class="fixed top-0 left-0 w-full h-full bg-white z-[999]">
          <Icon
            class="z-50 absolute cursor-pointer right-4 top-4"
            size="40"
            name="material-symbols:close"
            color="#000b26"
            @click="open = false"
          />

          <SidebarMenu />
        </div>
      </div>
      <div
        class="hidden lg:flex w-[250px] h-screen flex flex-col justify-between border-r"
      >
        <SidebarMenu />
        <UserItem />
      </div>
    </div>
  </div>
</template>
<script setup>
const open = ref(false);
</script>
