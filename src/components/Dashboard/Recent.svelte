<script>
  import Swal from "sweetalert2";
  import { onMount } from "svelte";
  import { redirect } from "page";
  import { user_URL } from "../../config";
  import { test } from "../../config";

  let obj = localStorage.getItem("token");
  onMount(prepare);

  const user = {
    userName: "",
    e_mail: "",
  };

  let tests;

  async function prepare() {
    if (obj == null) {
      window.location.replace("/sign-in");
    }
    obj = JSON.parse(obj);

    obj = obj.data.token;

    if (obj) {
      // redirect('/recent');
      const response = await fetch(`${user_URL}/data`, {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          Authorization: `Bearer ${obj}`,
        },
      });
      const data = await response.json();
      console.log(data);
      user.userName = data.data.name;
      user.e_mail = data.data.email;
      console.log(user);
    }
    getTests();
  }
  let welcomeVal = true;

  let hamVal = true;

  let toggle = () => {
    hamVal = !hamVal;
  };

  import RecentTest from "./show-detail-test.svelte";
  import ReTest from "./Re-test.svelte";

  let testsVal = true;

  let testData;
  let showTimer = true;
  let timer = 0;
  let testTimer = true;
  let test_Date;

  async function getTests() {
    const response = await fetch(`${test}/mytests`, {
      method: "POST",
      // mode:'no-cors',
      headers: {
        "Content-Type": "application/json",
        Authorization: `Bearer ${obj}`,
      },
    });
    const data = await response.json();
    tests = await data.data;

    console.log(tests);
  }

  async function getTestData(testId) {
    let test_id = testId;

    const response = await fetch(`${test}/testdetails`, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Authorization: `Bearer ${obj}`,
      },
      body: JSON.stringify({ test_id }),
    });
    const data = await response.json();
    testData = await data.data;

    console.log(data);
  }
  let retestVal = true;
</script>

<div class="body">
  <!-- svelte-ignore a11y-invalid-attribute -->
  <a href="" class="hamburger-menu" on:click={toggle}>
    {#if hamVal}
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="36"
        height="36"
        fill="#57B973"
        class="bi bi-list"
        viewBox="0 0 16 16"
      >
        <path
          fill-rule="evenodd"
          d="M2.5 12a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z"
        />
      </svg>
    {/if}
  </a>

  <div class="aside-parent">
    <div class="aside {hamVal ? '' : 'show-aside'}">
      {#if !hamVal}
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a href="" class="close" on:click={toggle}>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="34"
            height="34"
            fill="#57B973"
            class="bi bi-x"
            viewBox="0 0 16 16"
          >
            <path
              d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708z"
            />
          </svg>
        </a>
      {/if}

      <div class="main">
        <img src="https://picsum.photos/200/300" alt="" class="profile-image" />
        <h3 class="profile-name">{user.userName}</h3>
      </div>
      <div class="profile-links">
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a href="/app/home">
          <div class="i">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="20"
              height="20"
              fill="currentColor"
              class="bi bi-house-door-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M6.5 14.5v-3.505c0-.245.25-.495.5-.495h2c.25 0 .5.25.5.5v3.5a.5.5 0 0 0 .5.5h4a.5.5 0 0 0 .5-.5v-7a.5.5 0 0 0-.146-.354L13 5.793V2.5a.5.5 0 0 0-.5-.5h-1a.5.5 0 0 0-.5.5v1.293L8.354 1.146a.5.5 0 0 0-.708 0l-6 6A.5.5 0 0 0 1.5 7.5v7a.5.5 0 0 0 .5.5h4a.5.5 0 0 0 .5-.5z"
              />
            </svg>
            <span>Home</span>
          </div>
        </a>
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a href="/app/recent">
          <div class="i">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="20"
              height="20"
              fill="currentColor"
              class="bi bi-alarm-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M6 .5a.5.5 0 0 1 .5-.5h3a.5.5 0 0 1 0 1H9v1.07a7.001 7.001 0 0 1 3.274 12.474l.601.602a.5.5 0 0 1-.707.708l-.746-.746A6.97 6.97 0 0 1 8 16a6.97 6.97 0 0 1-3.422-.892l-.746.746a.5.5 0 0 1-.707-.708l.602-.602A7.001 7.001 0 0 1 7 2.07V1h-.5A.5.5 0 0 1 6 .5zm2.5 5a.5.5 0 0 0-1 0v3.362l-1.429 2.38a.5.5 0 1 0 .858.515l1.5-2.5A.5.5 0 0 0 8.5 9V5.5zM.86 5.387A2.5 2.5 0 1 1 4.387 1.86 8.035 8.035 0 0 0 .86 5.387zM11.613 1.86a2.5 2.5 0 1 1 3.527 3.527 8.035 8.035 0 0 0-3.527-3.527z"
              />
            </svg>
            <span>Recent</span>
          </div>
        </a>
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a href="/app/chart">
          <div class="i">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="20"
              height="20"
              fill="currentColor"
              class="bi bi-bar-chart-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M1 11a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v3a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1v-3zm5-4a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v7a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1V7zm5-5a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V2z"
              />
            </svg>
            <span>Chart</span>
          </div>
        </a>
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a href="/app/settings">
          <div class="i">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="20"
              height="20"
              fill="currentColor"
              class="bi bi-gear-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M9.405 1.05c-.413-1.4-2.397-1.4-2.81 0l-.1.34a1.464 1.464 0 0 1-2.105.872l-.31-.17c-1.283-.698-2.686.705-1.987 1.987l.169.311c.446.82.023 1.841-.872 2.105l-.34.1c-1.4.413-1.4 2.397 0 2.81l.34.1a1.464 1.464 0 0 1 .872 2.105l-.17.31c-.698 1.283.705 2.686 1.987 1.987l.311-.169a1.464 1.464 0 0 1 2.105.872l.1.34c.413 1.4 2.397 1.4 2.81 0l.1-.34a1.464 1.464 0 0 1 2.105-.872l.31.17c1.283.698 2.686-.705 1.987-1.987l-.169-.311a1.464 1.464 0 0 1 .872-2.105l.34-.1c1.4-.413 1.4-2.397 0-2.81l-.34-.1a1.464 1.464 0 0 1-.872-2.105l.17-.31c.698-1.283-.705-2.686-1.987-1.987l-.311.169a1.464 1.464 0 0 1-2.105-.872l-.1-.34zM8 10.93a2.929 2.929 0 1 1 0-5.86 2.929 2.929 0 0 1 0 5.858z"
              />
            </svg>
            <span>Settings</span>
          </div>
        </a>
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a
          href=""
          on:click={() => {
            console.log(obj);
            Swal.fire({
              title: "Are you sure?",
              text: "Are you sure that you want to log-out?",
              icon: "warning",
              showCancelButton: true,
              confirmButtonColor: "#3085d6",
              cancelButtonColor: "#d33",
              confirmButtonText: "Yes, log-out!",
            }).then((result) => {
              if (result.isConfirmed) {
                localStorage.removeItem("token");

                Swal.fire("Deleted!", "Your file has been deleted.", "success");
                window.location.replace("/sign-in");
              }
            });
          }}
        >
          <div class="i">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="20"
              height="20"
              fill="currentColor"
              class="bi bi-door-open-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M1.5 15a.5.5 0 0 0 0 1h13a.5.5 0 0 0 0-1H13V2.5A1.5 1.5 0 0 0 11.5 1H11V.5a.5.5 0 0 0-.57-.495l-7 1A.5.5 0 0 0 3 1.5V15H1.5zM11 2h.5a.5.5 0 0 1 .5.5V15h-1V2zm-2.5 8c-.276 0-.5-.448-.5-1s.224-1 .5-1 .5.448.5 1-.224 1-.5 1z"
              />
            </svg>
            <span>Log-out</span>
          </div>
        </a>
      </div>
    </div>
  </div>

  <main>
    {#if welcomeVal}
      <h1>Welcome {user.userName}</h1>
    {/if}

    <!-- <h3>No Recent Data</h3> -->

    {#if tests && testsVal}
      {#each tests as test}
        <div class="test-container">
          <div class="test-data">
            <div class="test-content">
              <h4>Subject : {test.metaData.test_name}</h4>
              <h6>Test date : {test.testDate}</h6>
            </div>
            <div class="d">
              you scored some percentile
              <h3>72%</h3>
            </div>
            <div class="test-buttons">
              <!-- svelte-ignore a11y-invalid-attribute -->
              <a
                href=""
                class="show-test-details"
                on:click={() => {
                  getTestData(test._id);
                  testsVal = false;
                  welcomeVal = false;
                }}
              >
                Show details
              </a>
              <!-- svelte-ignore a11y-invalid-attribute -->
              <a
                href=""
                class="retake-test"
                on:click={() => {
                  getTestData(test._id);
                  testsVal = false;
                  retestVal = false;
                  welcomeVal = false;
                }}
              >
                Re-attend Test
              </a>
            </div>
          </div>
        </div>
      {/each}
    {:else if testData}
      {#if retestVal}
        <RecentTest {testData} />
      {:else if testTimer}
        <div class="test-card">
          <div class="card">
            <button
              class="timer-on"
              on:click={() => {
                showTimer = !showTimer;
                timer = 0.5;
                if (showTimer) {
                  timer = 0;
                }
              }}>Timer-{showTimer ? "ON" : "OFF"}</button
            >

            {#if !showTimer}
              <div class="timer-cont">
                <button
                  class="minus"
                  on:click={() => {
                    if (timer) timer = timer - 0.5;
                  }}>-</button
                >
                <button class="timer">{timer} hr</button>
                <button
                  class="plus"
                  on:click={() => {
                    if (timer < 4) timer = timer + 0.5;
                  }}>+</button
                >
              </div>
            {/if}
            <!-- svelte-ignore a11y-img-redundant-alt -->

            <!-- svelte-ignore a11y-invalid-attribute -->
            <a
              href=""
              on:click={() => {
                testTimer = false;
                test_Date = new Date().toLocaleString([], { hour12: true });
              }}>Start</a
            >
            <div
              class="test-close"
              on:click={() => {
                testsVal = true;
                timer = 0;
                showTimer = true;
                retestVal = true;
              }}
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="34"
                height="34"
                fill="#57B973"
                class="bi bi-x"
                viewBox="0 0 16 16"
              >
                <path
                  d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708z"
                />
              </svg>
            </div>
          </div>
        </div>
      {:else}
        <ReTest {test_Date} {testData} token={obj} time={timer} />
      {/if}
    {/if}

    <!-- svelte-ignore a11y-invalid-attribute -->
    <a class="notification" href=""
      ><svg
        xmlns="http://www.w3.org/2000/svg"
        width="20"
        height="20"
        fill="currentColor"
        class="bi bi-bell-fill"
        viewBox="0 0 16 16"
      >
        <path
          d="M8 16a2 2 0 0 0 2-2H6a2 2 0 0 0 2 2zm.995-14.901a1 1 0 1 0-1.99 0A5.002 5.002 0 0 0 3 6c0 1.098-.5 6-2 7h14c-1.5-1-2-5.902-2-7 0-2.42-1.72-4.44-4.005-4.901z"
        />
      </svg></a
    >
  </main>
</div>

<style>
  img {
    max-width: 100%;
    height: auto;
  }
  a {
    text-decoration: none;
  }
  .body {
    display: flex;
    margin-top: -4rem;
    padding: 0;
  }
  .aside-parent {
    text-align: center;
    position: relative;
  }
  .aside {
    padding: 2.4rem 0;
    width: 20%;
    height: 100vh;
    color: #fff;
    background-image: linear-gradient(to right, #57b973, #2fa751);
    box-shadow: rgb(38, 57, 77) 0px 20px 30px -10px;
    overflow: hidden;
    position: fixed;
  }
  .aside .main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1.2rem;
  }
  .aside .profile-image {
    width: 3rem;
    height: 3rem;
    border-radius: 50%;
  }
  .aside .profile-links {
    display: flex;
    flex-direction: column;
    width: 100%;
    margin: 1.4rem auto;
  }
  .aside .profile-links a {
    width: 100%;
    text-decoration: none;
    color: #fff;
    font-weight: 700;
    font-size: 1.2rem;
    padding: 1.2rem 0;
    transition: 0.1s all ease-in;
    display: flex;
    text-align: left;
    padding-left: 20%;
    margin: 0;
  }
  .aside .profile-links a .i {
    display: flex;
    align-items: center;
    gap: 2.4rem;
  }
  /* .aside .profile-links a span {
      text-align: center;
      padding: 0 3rem;
  } */
  .aside .profile-links a:hover {
    background-color: #2fa751;
  }

  main {
    width: 80%;
    margin-left: auto;
    text-align: center;
    max-height: 100%;
    min-height: 100vh;
    padding: 0 2rem;
    background-color: #d9e4f5;
    background-image: linear-gradient(315deg, #d9e4f5 0%, #f5e3e6 74%);
  }
  main h1 {
    margin-top: 1rem;
    background: -webkit-linear-gradient(#eee, #333);
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  main h3 {
    margin: 1rem;
    background: -webkit-linear-gradient(#eee, #333);
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  main .test-container {
    width: 80%;
    margin: 1.2rem auto;
    padding: 1.8rem 3rem;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  }
  main .test-container .test-data {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  main .test-container .test-data h4 {
    font-size: 1.8rem;
    color: #2fa751;
  }
  main .test-container .test-data h6 {
    margin: 1rem;
  }
  main .test-container .test-data .test-buttons {
    display: flex;
    flex-direction: column;
  }
  main .test-container .test-data a {
    text-decoration: none;
    padding: 6px 14px;
    background-color: #57b973;
    color: #fff;
    border-radius: 6px;
    margin: 6px 0;
  }
  .notification {
    position: absolute;
    right: 12px;
    top: 6px;
  }
  .hamburger-menu {
    position: absolute;
    top: 5px;
    left: 5px;
    cursor: pointer;
    border-radius: 3px;
    overflow: hidden;
    display: none;
  }
  .close {
    position: absolute;
    top: 5px;
    right: 5px;
    cursor: pointer;
    overflow: hidden;
    display: none;
  }
  .test-close {
    position: absolute;
    right: 12px;
    top: 6px;
    cursor: pointer;
  }
  .card {
    width: 90%;
    margin: 0 auto;
    margin-top: 2.4rem;
    text-align: center;
    background-color: rgb(255, 255, 255);
    color: #444;
    border-radius: 6px;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    padding: 1rem 0;
    position: relative;
  }
  button {
    border-radius: 3px;
  }

  .card .timer-on {
    margin: 0.2rem auto;
  }
  .card .timer-cont {
    margin: 0.2rem 0;
  }
  .card .timer-cont .timer {
    padding: 8px 12px;
    margin: 0 0.2rem;
  }
  .card .timer-cont .plus,
  .card .timer-cont .minus {
    padding: 3px 8px;
  }
  .card a {
    padding: 0.4rem 5rem;
    background-color: #57b973;
    border-radius: 4px;
    color: #fff;
    margin: 0.6rem auto;
    display: inline-block;
    margin-bottom: 1rem;
    transition: 0.12s all ease-in;
  }
  .card a:hover {
    background-color: #2fa751;
  }
  @media (max-width: 1100px) {
    .aside .profile-links a svg {
      display: none;
    }
    .aside .profile-links a {
      text-align: center;
      justify-content: center;
      padding-left: 0;
    }
  }
  @media (max-width: 960px) {
    .aside {
      display: none;
      position: fixed;
    }
    .hamburger-menu {
      display: block;
    }
    .close {
      display: block;
    }
    .show-aside {
      display: block;
      width: 30%;
    }
    main {
      width: 100%;
    }
    main .test-container {
      width: 90%;
      padding: 1.8rem 3rem;
    }
    main .test-container .test-data {
      display: block;
      text-align: center;
    }
  }
  @media (max-width: 760px) {
    .aside .profile-links a svg {
      display: block;
    }
    .aside .profile-links a span {
      display: none;
    }
    main .test-container {
      width: 90%;
      padding: 1.6rem 2rem;
    }
  }
  @media (max-width: 600px) {
    /* main {
      height: 100vh;
    } */
    main {
      height: 100%;
    }

    .show-aside {
      width: 36%;
    }
  }
</style>
