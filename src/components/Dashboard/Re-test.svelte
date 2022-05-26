<script>
  import { test } from "../../config";
  export let testData;
  export let token;

  let questionPaper = testData.questionPaper;
  let subject = testData.metaData.test_name;

  subject = subject.toLowerCase();

  // questionPaper = questionPaper.slice(0, 4);
  console.log(questionPaper);
  import Chart from "./chart.svelte";
  export let time;
  export let test_Date;
  const old_count = [];

  old_count.push(time * 3600);

  let save = { questionPaper };

  let qNo = 0;
  let col = "";
  let val = true;
  let selectedAnswers = [];
  let radioSlectionChecker;
  function getAnswer() {
    let answers = document.querySelectorAll(".answer");
    answers.forEach((answer) => {
      if (answer.checked) {
        selectedAnswers.push(parseInt(answer.id));
        radioSlectionChecker = true;
      }
      answer.checked = false;
    });
    if (!radioSlectionChecker) {
      selectedAnswers.push(5);
    }
    radioSlectionChecker = false;
  }
  time = time * 3600 - 1;
  let seconds = "0";
  let minutes = "0";
  let hours = "0";
  let minuteSecond;
  let counter_func = setInterval(() => {
    if (time > 0) {
      seconds = time % 60;
      minuteSecond = (time - seconds) / 60;
      minutes = minuteSecond % 60;
      hours = (minuteSecond - minutes) / 60;
    }
    if (time > 0) {
      time--;
    }
  }, 1000);
  let seconds2 = "0";
  let minutes2 = "0";
  let hours2 = "0";
  let minuteSecond2;
  let resultTimeVal = false;
  const resultCount = () => {
    let time2 = old_count[0] - (time + 1);
    seconds2 = time2 % 60;
    minuteSecond2 = (time2 - seconds2) / 60;
    minutes2 = minuteSecond2 % 60;
    hours2 = (minuteSecond2 - minutes2) / 60;
    resultTimeVal = true;
  };
  let answerSheet = false;
  let correctAnswersArray = [];
  let wrongAnswersArray = [];
  let notSelectedAnswersArray = [];
  let correctAnswer;
  let wrongAnswer;
  let notSelectedAnswer;
  let totalQuestions;
  let questionAttempted;

  const createChartVal = () => {
    // for (let i = 0; i < selectedAnswers.length; i++) {
    //   if (selectedAnswers[i] == result.question[i].ans) {
    //     correctAnswers.push(selectedAnswers[i])
    //   }else if (selectedAnswers[i] == 'Not-Selected') {
    //     notSelectedAnswers.push(selectedAnswers[i])
    //   }else {
    //     wrongAnswers.push(selectedAnswers[i])
    //   }

    // }

    let i = 0;
    selectedAnswers.forEach((selectedAnswer) => {
      if (selectedAnswer == questionPaper[i].answer) {
        correctAnswersArray.push(selectedAnswer);
      } else if (selectedAnswer == 5) {
        notSelectedAnswersArray.push(selectedAnswer);
      } else {
        wrongAnswersArray.push(selectedAnswer);
      }
      i++;
    });
    correctAnswer = correctAnswersArray.length;
    wrongAnswer = wrongAnswersArray.length;
    notSelectedAnswer = notSelectedAnswersArray.length;

    totalQuestions = correctAnswer + wrongAnswer + notSelectedAnswer;
    questionAttempted = correctAnswer + wrongAnswer;
  };

  async function saveTest(savingTest) {
    const response = await fetch(`${test}/save`, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Authorization: `Bearer ${token}`,
      },
      body: JSON.stringify(savingTest),
    });
    const data = await response.json();

    console.log(data);
    if (data.message == "answer paper saved!") alert("Test saved Successfully");
  }
</script>

<!-- style="background-color: { val ? 'inherit'  : '#57B973'};" -->
<section>
  {#if time > 0}
    <div class="timer">
      <h1>
        {"0" + hours}:{minutes < 10 ? "0" + minutes : minutes}:{seconds < 10
          ? "0" + seconds
          : seconds}
      </h1>
      {#if resultTimeVal}
        <h3>You finished Test in {hours2}Hrs:{minutes2}Mins:{seconds2}Secs</h3>
      {/if}
    </div>
  {/if}
  {#if val}
    <main>
      <div class="question-container">
        <div class="Question">
          {#if questionPaper[qNo].image}
            <h5>
              {qNo + 1}.
              <img
                src={questionPaper[qNo].image}
                alt="question"
                class="question-image"
              />
            </h5>
          {:else}
            <h5>{qNo + 1}. {questionPaper[qNo].question}</h5>
          {/if}
        </div>
        <div class="answers">
          <ol>
            <li>
              <input type="radio" class="answer" name="answer" id="1" /><label
                for="1"
                >1.
                {#if questionPaper[qNo].options[0][0]}
                  <img
                    class="option-image"
                    src={questionPaper[qNo].options[0][0]}
                    alt=""
                  />
                {:else}
                  {questionPaper[qNo].options[0][1]}
                {/if}
              </label>
            </li>

            <li>
              <input type="radio" class="answer" name="answer" id="2" /><label
                for="2"
                >2.{#if questionPaper[qNo].options[1][0]}
                  <img
                    class="option-image"
                    src={questionPaper[qNo].options[1][0]}
                    alt=""
                  />
                {:else}
                  2.{questionPaper[qNo].options[1][1]}
                {/if}</label
              >
            </li>
            <li>
              <input type="radio" class="answer" name="answer" id="3" /><label
                for="3"
                >3.{#if questionPaper[qNo].options[2][0]}
                  <img
                    class="option-image"
                    src={questionPaper[qNo].options[2][0]}
                    alt=""
                  />
                {:else}
                  2.{questionPaper[qNo].options[2][1]}
                {/if}</label
              >
            </li>
            <li>
              <input type="radio" class="answer" name="answer" id="4" /><label
                for="4"
                >4.{#if questionPaper[qNo].options[3][0]}
                  <img
                    class="option-image"
                    src={questionPaper[qNo].options[3][0]}
                    alt=""
                  />
                {:else}
                  2.{questionPaper[qNo].options[3][1]}
                {/if}</label
              >
            </li>
          </ol>
        </div>
      </div>
      <!-- svelte-ignore a11y-invalid-attribute -->
      <a
        on:click={() => {
          qNo && qNo--;
        }}
        href="">Prev</a
      >
      <!-- svelte-ignore a11y-invalid-attribute -->
      {#if qNo == questionPaper.length - 1}
        <a
          on:click={() => {
            getAnswer();
            clearInterval(counter_func);
            val = false;
            resultCount();
            createChartVal();
            console.log(selectedAnswers);
          }}
          href="">Submit</a
        >
      {:else}
        <a
          on:click={() => {
            getAnswer();
            qNo++;
          }}
          href="">Next</a
        >
      {/if}
    </main>
  {:else}
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
                <!-- {#if }
                {/if} -->
                <!-- {#if selectedAnswers[i] !== question.answer}
                  
                {/if} -->
                <h5 class="answer">
                  Correct answer : {#if question.options[question.answer - 1][0]}
                    <img
                      src={question.options[question.answer - 1][0]}
                      alt=""
                    />
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
    </div>
    <a
      href="/app"
      class="back-to-home"
      on:click={() => {
        window.location.replace("http://localhost:8080/app");
      }}>Back to Home</a
    >
  {/if}
  {#if !val}
    <div
      class="save"
      on:click={() => {
        save.selectedAnswers = [...selectedAnswers];
        save.metaData = {
          correct_answers: correctAnswer,
          wrong_answers: wrongAnswer,
          not_selected_answers: notSelectedAnswer,
          test_name: subject,
        };
        save.testDate = test_Date;
        console.log(JSON.stringify(save));
        saveTest(save);
      }}
    >
      <!-- svelte-ignore a11y-invalid-attribute -->
      <a href="" class="save-btn"><i class="bi bi-save"><p>save</p></i></a>
    </div>
  {/if}
</section>

<style>
  section {
    /* margin-top: -4rem; */
    padding: 0;
  }
  main {
    margin: 2rem auto;
    text-align: center;
  }
  .question-container {
    text-align: left;
    padding: 2rem 2.4rem;
    background-color: rgb(227, 238, 238);
    width: 80%;
    margin: 0 auto;
    border-radius: 6px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  }
  .question-container h5 {
    margin-left: 2rem;
  }
  .question-container h5 .question-image {
    width: 200px;
    height: auto;
  }
  main a {
    margin: 3.2rem 8%;
    text-decoration: none;
    color: white;
    padding: 0.6rem 8%;
    background-color: #57b973;
    border-radius: 5px;
    display: inline-block;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    transition: all 0.14s ease-in;
  }

  main a:hover {
    background-color: #2fa751;
  }
  .question-container h5 {
    margin: 2rem;
  }
  ol {
    list-style: none;
  }

  li {
    margin: 1.6rem 0;
    width: 70%;
  }
  li:hover {
    background-color: #9cf0b4;
  }
  input {
    margin-right: 10px;
  }
  input[name="answer"] {
    accent-color: #57b973;
    filter: contrast(0.8);
  }
  label,
  input {
    cursor: pointer;
  }
  .result {
    width: 85%;
    margin: 0.2rem auto;
    padding: 0.2rem 0;
    text-align: center;
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
  .timer {
    text-align: center;
    padding: 1rem 0;
  }
  .timer h1 {
    padding: 4px 10px;
    color: rgb(204, 15, 15);
    margin: 0 auto;
    display: inline-block;
  }
  .timer h3 {
    color: #777;
    font-size: 1rem;
  }

  .save-btn {
    text-decoration: none;
    position: fixed;
    bottom: 1.6rem;
    right: 3rem;
    color: #35b945;
    font-size: larger;
    text-align: center;
  }
  .save-btn p {
    margin-top: -6px;
    font-size: medium;
  }
  @media (max-width: 1000px) {
    .question-container {
      width: 75%;
      padding: 1rem;
    }
    .result {
      width: 85%;
    }
    .question-container ol li {
      width: 100%;
    }
    main a {
      margin: 1.8rem 4%;
    }
  }
  @media (max-width: 768px) {
    .question-container {
      width: 85%;
    }
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
