<script setup  >
import Chart from 'chart.js/auto';
import { ref, onMounted } from 'vue'

function l(variable){
    return console.log(variable)
}

var initialValueInvested = 10000;
var currentValueInvested = 10000;
var interestSelicRateByYear = 13.75 * 0.01; // 13.75 
const currentYear = new Date().getUTCFullYear();
const todayDateString = new Date().toLocaleDateString()
const currentMonth =  todayDateString.slice(3,5);
const annualInterestSelicRateCode = 1178;

setTimeout(function(){
  data.shift()
  l(data)
},3000)

const data = [
    { year: currentYear+1, value: 0 },
    { year: currentYear+2, value: 0 },
    { year: currentYear+3, value: 0 },
    { year: currentYear+4, value: 0  },
    { year: currentYear+5, value: 0  },
    { year: currentYear+6, value: 0 }, 
    ];

var numberOfItems = data.lenght; 

//var newData = data.splice(1,data.length)


onMounted(() => {
 

    data.map( item =>  {
    currentValueInvested = (currentValueInvested * interestSelicRateByYear) + currentValueInvested;   
    item.value = currentValueInvested;
    //l(currentValueInvested)
   
    }  )

    l(initialValueInvested)
    data.unshift( { year: currentYear, value: initialValueInvested })
    
  new Chart(
    document.getElementById('myChart'),
    {
      type: 'line',
      data: {
        labels: data.map(row => row.year),
        datasets: [
          {
            label: 'Investment value by year',
            data: data.map(row => Math.floor(row.value)),
            borderColor: '#3498db'

          }, 
                  ]
      }
    }
  );


})


</script>
<template>
    <div>
        <canvas id="myChart" ></canvas> 
    </div>
</template>
<style scoped>
 #myChart{
  width: 80vh;
}

</style>