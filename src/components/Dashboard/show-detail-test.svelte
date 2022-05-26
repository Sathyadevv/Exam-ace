<script>
  export let testData;

  import Chart from "./chart.svelte";

  let answerSheet = false;
  let questionPaper = testData.questionPaper;
  let test_Date = testData.testDate;

  let selectedAnswers = testData.selectedAnswers;
  let correctAnswer = testData.metaData.correct_answers;
  let wrongAnswer = testData.metaData.wrong_answers;
  let notSelectedAnswer = testData.metaData.not_selected_answers;
  let totalQuestions = correctAnswer + wrongAnswer + notSelectedAnswer;
  let questionAttempted = correctAnswer + wrongAnswer;
</script>

<section>
  <div class="result">
    <div class="header">
      <h2>Result</h2>
      <h4><span style="font-weight: 900;">Test-date :</span> {test_Date}</h4>
      <div class="score-card">
        <h3>You Scored 68% of 100</h3>
        <div class="chart-container">
          <Chart {correctAnswer} {wrongAnswer} {notSelectedAnswer} />
          <div class="chart-text">
            <h5>
              Questions Attempted <span
                >{questionAttempted}/{totalQuestions}</span
              >
            </h5>
            <h6>
              <span class="bullet bullet-1" /> Correct Answers
              <span>{correctAnswer}/{questionAttempted}</span>
            </h6>
            <h6>
              <span class="bullet bullet-2" /> Wrong Answers
              <span>{wrongAnswer}/{questionAttempted}</span>
            </h6>
            <h6>
              <span class="bullet bullet-3" /> Questions Not Attempted
              <span>{notSelectedAnswer}/{totalQuestions}</span>
            </h6>
            <!-- svelte-ignore a11y-invalid-attribute -->
            <a
              on:click={() => {
                answerSheet = true;
              }}
              href="#">Analyze Test</a
            >
          </div>
        </div>
      </div>
    </div>
    {#if answerSheet}
      <div class="answer-sheet">
        <div class="questions">
          {#each questionPaper as question, i}
            <div class="results">
              <h5>{i + 1}. {question.question}</h5>

              {#if selectedAnswers[i] == question.answer}
                <h5 style="color: #57b973;">
                  Your Answer :
                  {#if question.options[question.answer - 1][0]}
                    <img
                      src={question.options[question.answer - 1][0]}
                      alt=""
                    />
                  {:else}{question.options[question.answer - 1][1]}
                  {/if}
                </h5>{:else if selectedAnswers[i] == 5}
                <h5 style="color: red;">You did't select Any answer.</h5>
              {:else}<h5 style="color: red;">
                  Your Answer : {#if question.options[selectedAnswers[i] - 1][0]}
                    <img
                      src={question.options[selectedAnswers[i] - 1][0]}
                      alt=""
                    />
                  {:else}
                    {question.options[selectedAnswers[i] - 1][1]}
                  {/if}
                </h5>
              {/if}

              <h5 class="answer">
                Correct answer : {#if question.options[question.answer - 1][0]}
                  <img src={question.options[question.answer - 1][0]} alt="" />
                {:else}
                  {question.options[question.answer - 1][1]}
                {/if}
              </h5>
              <h6>Explanation : {question.explanation}</h6>
            </div>
          {/each}
        </div>
      </div>
    {/if}
    <!-- </div> -->
    <a
      href="/app/"
      class="back-to-home"
      on:click={() => {
        window.location.href("http://localhost:8080/app/recent");
      }}>Back to Home</a
    >
  </div>
</section>

<style>
  section {
    /* margin-top: -4rem; */
    padding: 0;
  }

  .result {
    width: 85%;
    margin: 0.2rem auto;
    padding: 0.2rem 0;
    text-align: center;
    height: 100%;
  }
  .result .header .score-card {
    background-color: #fff;
    padding: 2rem 3rem;
    border-radius: 8px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    color: #555;
    margin: 2rem 0;
    background-color: #d9e4f5;
  }
  .score-card .chart-container {
    margin: 2rem 0;
    display: flex;
    align-items: center;
    justify-content: space-around;
  }
  .score-card h3 {
    font-size: 2.6rem;
  }
  .score-card h5 {
    font-size: 1.6rem;
  }
  .score-card h6 {
    margin: 1.6rem 0;
  }
  .score-card .chart-container h6 .bullet {
    display: inline-block;
    width: 12px;
    height: 9px;
    margin: 2px 0;
    border-radius: 1px;
  }
  .score-card .chart-container h6 .bullet-1 {
    background-color: #35b945;
  }
  .score-card .chart-container h6 .bullet-2 {
    background-color: #fc291ed8;
  }
  .score-card .chart-container h6 .bullet-3 {
    background-color: #d04ed6;
  }
  .score-card .chart-container a {
    display: inline-block;
    padding: 10px 22px;
    border-radius: 4px;
    text-decoration: none;
    background-color: #57b973;
    color: #fff;
    transition: 0.12s all;
    margin-top: 1rem;
  }
  .back-to-home {
    display: inline-block;
    padding: 10px 22px;
    border-radius: 4px;
    text-decoration: none;
    background-color: #57b973;
    color: #fff;
    transition: 0.12s all;
    margin: 0 auto;
    margin-bottom: 1rem;
    /* position: absolute;
      top: 0.3rem;
      left: 0.3rem; */
  }
  .back-to-home:hover {
    opacity: 0.86;
  }
  .score-card .chart-container a:hover {
    background-color: #35b945;
  }
  .result h2 {
    color: #2fa751;
    font-size: 5rem;
  }
  .result h4 {
    font-size: 0.9rem;
    opacity: 0.7;
  }
  .result .questions {
    margin: 2rem 0;
    text-align: left;
  }
  .result .questions h5 {
    margin: 1.2rem 0;
  }
  .result .questions .answer {
    color: #57b973;
  }
  .questions .results {
    margin-top: 0.6rem;
    background-color: #d9e4f5;
    padding: 2.6rem 3rem;
    border-radius: 8px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  }

  @media (max-width: 1000px) {
    .result {
      width: 85%;
    }
  }
  @media (max-width: 768px) {
    .result h2 {
      font-size: 3.6rem;
    }
    .score-card .chart-container {
      display: block;
    }
    .score-card h3 {
      font-size: 2rem;
    }
    .back-to-home {
      font-size: 12px;
    }
  }
</style>
