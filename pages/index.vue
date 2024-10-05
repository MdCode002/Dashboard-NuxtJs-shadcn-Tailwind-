
<script setup>
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';

const loading = ref(false);

const listTabs = ref([
  {
    label: 'Today',
    value: 'today',
    content: resolveComponent("TabsToday"),
  },
  {
    label: 'This Week',
    value: 'week',
    content: 'This Week',
  },
  {
    label: 'This Year',
    value: 'year',
    content: 'This Year',
  },
]);

let data = ref([
  16.0, 18.2, 23.1, 27.9, 32.2, 36.4, 39.8, 38.4, 35.5, 29.2,
  22.0, 17.8,
]);


let currentCategory = ref('today');


function generateRandomData(number = 23) {
  let values = [];
  for (let i = 0; i < number + 1; i++) {
    values.push(Math.floor(Math.random() * 100));
  }
  console.log(values);
  data.value = values;
  return values;
}

function setCategory(cat) {
  currentCategory.value = cat;
  switch (cat) {
    case 'today':
      generateRandomData(23);
      break; // Ajoutez break ici
    case 'week':
      generateRandomData(6);
      break; // Ajoutez break ici
    case 'year':
      generateRandomData(11);
      break; // Ajoutez break ici
    default:
      generateRandomData(23);
      break; // Ajoutez break ici
  }
}

onMounted(() => {
  generateRandomData();
});
</script>


<template>
  <div class="grid gap-8">
    <header class="flex item-start justify-between">
      <div>
        <p>Hi Mouhamed welcome back</p>
        <h1>Dashboard</h1>
      </div>
      <div class="bg-neutral-200 w-[80px] h-[30px]"></div>
    </header>
    <main class="grid gap-4">
      <Tabs :default-value="listTabs[0].value">
        <TabsList class="w-[400px]">
          <TabsTrigger
            v-for="(listTab, index) in listTabs"
            :key="index"
            :value="listTab.value"
            @click="setCategory(listTab.value)"
          >
            {{ listTab.label }}
          </TabsTrigger>
        </TabsList>
        <TabsContent
          v-for="(listTab, index) in listTabs"
          :key="index"
          :value="listTab.value"
        >
          <Chart :currentCategory="currentCategory" :data="data"/>
        </TabsContent>
      </Tabs>
    </main>
    <footer>
      <div class="flex items-center gap-2">
        <div class="bg-neutral-200 h-[200px] w-full"></div>
        <div class="bg-neutral-200 h-[200px] w-full"></div>
        <div class="bg-neutral-200 h-[200px] w-full"></div>
      </div>
    </footer>
  </div>
</template>

