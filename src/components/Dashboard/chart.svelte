<script>
  export let correctAnswer;
  export let wrongAnswer;
  export let notSelectedAnswer;

  import { onMount } from "svelte";
  let ctx;

  onMount(async () => {
    const myChart = new Chart(ctx, {
      type: "doughnut",
      data: {
        datasets: [
          {
            label: "# of Votes",
            data: [correctAnswer, wrongAnswer, notSelectedAnswer],
            backgroundColor: ["#35b945", "#fc291ed8", "#d04ed6"],
            borderWidth: 1,
          },
        ],
      },
    });
  });
</script>

<div class="containerr">
  <canvas id="myChart" bind:this={ctx} />
</div>

<style>
  .containerr {
    width: 40%;
    height: auto;
    margin: 1.4rem auto;
  }
  @media (max-width: 768px) {
    .containerr {
      width: 60%;
    }
  }
</style>
