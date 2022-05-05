<div class="containerr">
    <canvas id="myChart"  bind:this={ctx}></canvas>

</div>
<script>
export let correctAnswer;
export let wrongAnswer;
export let notSelectedAnswer;


import {onMount} from 'svelte';
let ctx;

onMount(
    
    async ()=> {
        const myChart = new Chart(ctx, {
    type: 'doughnut',
    data: {
        datasets: [{
            label: '# of Votes',
            data: [correctAnswer, wrongAnswer, notSelectedAnswer],
            backgroundColor: [
                '#35b945',
                '#fc291ed8',
                '#d04ed6'
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
    // options: {
    //     scales: {
    //         y: {
    //             beginAtZero: true
    //         }
    //     }
    // }
});
    }
)


</script>

 
<style>
    .containerr {
        width: 40%;
        height: auto;
    }
    
</style>
 