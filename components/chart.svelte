<div class="container">
    <canvas id="myChart"  bind:this={ctx}></canvas>

</div>
<script>

import {onMount} from 'svelte';

let ctx;

onMount(
    async ()=> {
        const myChart = new Chart(ctx, {
    type: 'doughnut',
    data: {
        labels: ['Correct ans','Wrong ans','Not attempted'],
        datasets: [{
            label: '# of Votes',
            data: [12, 19, 3],
            backgroundColor: [
                '#008000',
                '#d00000',
                '#7209b7'
            ],
            // borderColor: [
            //     'rgba(255, 99, 132, 1)',
            //     'rgba(54, 162, 235, 1)',
            //     'rgba(255, 206, 86, 1)',
            //     'rgba(75, 192, 192, 1)',
            //     'rgba(153, 102, 255, 1)',
            //     'rgba(255, 159, 64, 1)'
            // ],
            borderWidth: 1
        }]
    },
    options: {
        scales: {
            y: {
                beginAtZero: true
            }
        }
    }
});
    }
)


</script>

 
<style>
    .container {
        width: 40%;
        height: auto;
        margin: 2rem auto;
        padding: 2rem;
    }
    
</style>
 