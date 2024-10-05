<script setup>
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs";

const loading = ref(false);
let data = ref([]);

const listTabs = ref([
  {
    label: "Today",
    value: "today",
    content: resolveComponent("TabsToday"),
  },
  {
    label: "This Week",
    value: "week",
    content: "This Week",
  },
  {
    label: "This Year",
    value: "year",
    content: "This Year",
  },
]);

let currentCategory = ref("today");

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
    case "today":
      generateRandomData(23);
      break; // Ajoutez break ici
    case "week":
      generateRandomData(6);
      break; // Ajoutez break ici
    case "year":
      generateRandomData(11);
      break; // Ajoutez break ici
    default:
      generateRandomData(23);
      break; // Ajoutez break ici
  }
}

const cards = [
  {
    title: "Sales",
    progression: 12,
    amount: 1244.43,
    label: "View sales",
    description: "Sales of March 2024",
    icon: "solar:ticket-sale-outline",
  },
  {
    title: "Refunds",
    progression: 8,
    amount: 84.44,
    label: "View refunds",
    description: "Refunds since beginning of year",
    icon: "heroicons-outline:receipt-refund",
  },
  {
    title: "Payouts",
    progression: 14,
    amount: 899.99,
    label: "View payouts",
    description: "Payouts of this week",
    icon: "tabler:zoom-money",
  },
];
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
      <ProductNew />
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
          <Chart :currentCategory="currentCategory" :data="data" />
        </TabsContent>
      </Tabs>
    </main>
    <footer>
      <div class="flex items-center gap-2">
        <Card v-for="(card, i) in cards" :key="i" :card="card" />
      </div>
    </footer>
  </div>
</template>
