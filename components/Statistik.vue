<template>
  <div>
    <canvas id="statistik"></canvas>
  </div>
  </template>

  <script setup>
  import Chart from 'chart.js/auto'

  const labels = [
    'January',
    'February',
    'March',
    'April',
    'May',
    'June',
  ];

  const data = {
    labels: labels,
    datasets: [{
      label: 'My First dataset',
      backgroundColor: 'rgb(255, 99, 132)',
      borderColor: 'rgb(255, 99, 132)',
      data: [10, 15, 20, 10, 10, 20, 45],
    }]
  };

  const config = {
    type: 'bar',
    data: data,
    options: {}
  };


onMounted(( ) => {
  const myChart = new Chart(
    document.getElementById('statistik'),
    config
  );
})
</script>

