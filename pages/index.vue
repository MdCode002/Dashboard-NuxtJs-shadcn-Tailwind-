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
          <highchart :options="chartOptions" />
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

let categories = ref({
  today: [
    '00:00', '01:00', '02:00', '03:00', '04:00', '05:00', '06:00', '07:00',
    '08:00', '09:00', '10:00', '11:00', '12:00', '13:00', '14:00', '15:00',
    '16:00', '17:00', '18:00', '19:00', '20:00', '21:00', '22:00', '23:00',
  ],
  week: ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'],
  year: [
    'January', 'February', 'March', 'April', 'May', 'June', 'July', 'August',
    'September', 'October', 'November', 'December',
  ],
});

let currentCategory = ref('today');

const chartOptions = computed(() => {
  return {
    chart: {
      type: 'line',
    },
    title: {
      text: '',
    },
    xAxis: {
      categories: categories.value[currentCategory.value], // Correction ici
    },
    yAxis: {
      title: {
        text: '',
      },
    },
    plotOptions: {
      line: {
        marker: {
          enabled: false,
        },
        dataLabels: {
          enabled: false,
        },
        enableMouseTracking: true,
      },
    },
    series: [{
      name: 'line',
      linewidth: '4px',
      data: data.value,
      color: {
        linearGradient: {},
        stops: [
          [0, 'rgba(252, 176, 69, 1)'],
          [0.33, 'rgba(253, 29, 29, 1)'],
          [0.66, 'rgba(131, 58, 180, 1)'],
          [1, 'rgba(29, 217, 83, 1)'],
        ],
      },
    }],
  };
});

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
