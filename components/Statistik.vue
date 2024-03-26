<template>
  <div>
    <canvas id="statistik"></canvas>
  </div>
</template>

<script setup>
import Chart from "chart.js/auto";

const labels = ["January", "February", "March", "April", "May", "June"];

const data = {
  labels: labels,
  datasets: [
    {
      label: "My First dataset",
      data: [10, 15, 20, 10, 10, 20, 45],
      backgroundColor: [
        "rgba(131, 172, 234, 0.8)",
        "rgba(155, 224, 239, 0.8)",
        "rgba(108, 200, 200, 0.8)",
        "rgba(131, 172, 234, 0.8)",
        "rgba(131, 172, 234, 0.8)",
        "rgba(108, 200, 200, 0.8)",
      ],
    },
  ],
};

const config = {
  type: "bar",
  data: data,
  options: {},
};

onMounted(() => {
  const myChart = new Chart(document.getElementById("statistik"), config);
});
</script>
