<script setup  > 
import ChartComponent from './components/ChartComponent.vue';  
import { ref } from 'vue'
var showChartVariable = ref(false); 
 
 

</script>

<template>
<main>

<h2>Show Selic return on investment </h2>
<h2>Initial value: 10000 over 6 years</h2>


<button @click="showChartVariable = !showChartVariable"> Display chart </button>

<div v-if="showChartVariable" > 
  <ChartComponent /> 
</div>
<div v-else>
  Try to see the charts
</div>

  </main> 
</template>
 