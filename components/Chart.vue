<script setup>
const props = defineProps(["currentCategory", "data"]);
const data = ref(props.data);
const currentCategory = ref(props.currentCategory);
console.log(data.value);

const categories = ref({
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

const chartOptions = computed(() => {
  return {
    chart: {
      type: 'line',
    },
    title: {
      text: '',
    },
    xAxis: {
      categories: categories.value[currentCategory.value],
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
      name: 'ligne',
      lineWidth: 4,
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

</script>
<template>
    <div class="border p-4 rounded bg">
        <highchart v-if="data.length > 0" :options="chartOptions" />
    </div>
</template>