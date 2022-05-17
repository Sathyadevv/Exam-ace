<script>
  import Test from "./test.svelte";
  import swal from 'sweetalert';

  let val = true;
  let val2 = true;
  let paymentVal;
  let test_catgry = "";
  let test_arr = [
    { image: "../assets/icons/icons8-medical-64.png", exam: "NEET" },
    { image: "../assets/icons/icons8-chemistry-64.png", exam: "JAM" },
    { image: "../assets/icons/icons8-engineering-64.png", exam: "JEE" },
  ];
  let showTimer = true;
  let timer = 0;
  let testDate;
  let hamVal = true;

  let obj = localStorage.getItem('token')
  

  let toggle = () => {
    hamVal = !hamVal;
  };
  const getPlan = async (plan) => {
    let buyingClient = {
      clientID : '',
      plan : plan
    }
    const response = await fetch(`${server_URL}/${path}`, {
      method: "POST",
      headers: {
    Authorization: `Bearer ${obj.token}`
  }
    });
    const data = await response.json();

    console.log(data)
   
  }
</script>

{#if val}
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
        <h3 class="profile-name">Admin name</h3>
      </div>
      <div class="profile-links">
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a href="">
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
        <a href="">
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
        <a href="">
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
        <a href="">
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
        <a href="">
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
    <main>
      <h1>Welcome Admin</h1>

      <h3>Attend TEST</h3>
      {#if paymentVal}
      {#if val2}
      <!-- svelte-ignore a11y-invalid-attribute -->
      <a
        href=""
        class="test-attend"
        on:click={() => {
          val2 = false;
          test_catgry = 0;
        }}
      >
        NEET
      </a>
      <!-- svelte-ignore a11y-invalid-attribute -->
      <a
        href=""
        class="test-attend"
        on:click={() => {
          val2 = false;
          test_catgry = 1;
        }}
      >
        JAM
      </a>
      <!-- svelte-ignore a11y-invalid-attribute -->
      <a
        href=""
        class="test-attend"
        on:click={() => {
          val2 = false;
          test_catgry = 2;
        }}
      >
        JEE
      </a>
    {:else}
      <div class="test-card">
        <div class="card">
          <h3>{test_arr[test_catgry].exam}</h3>

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
          <img src={test_arr[test_catgry].image} alt="test-category-image" />

          <!-- svelte-ignore a11y-invalid-attribute -->
          <a
            on:click={() => {
              val = false;
              testDate = new Date().toLocaleString([], { hour12: true });
            }}
            href="">Start</a
          >
        </div>
      </div>
    {/if}
      {/if}
      

      <div class="status-cards">
        <div class="status-card">
          <h4>Trial</h4>
          <h2>Free</h2>
          <h6>One Test</h6>
          <h5>50 Questions</h5>
          <!-- svelte-ignore a11y-invalid-attribute -->
          <a class="free" href="" >Start Test</a>
        </div>
        <div class="status-card">
          <h4>Plan-A</h4>
          <h2>₹ 299</h2>
          <h6>One Month</h6>
          <h5>Unlimited-Tests</h5>
          <!-- svelte-ignore a11y-invalid-attribute -->
          <a class="one" href="" on:click={() => {getPlan('Plan-A')}}>Get Plan</a>
        </div>
        <div class="status-card">
          <h4>Plan-B</h4>
          <h2>₹ 599</h2>
          <h6>Three Months</h6>
          <h5>Unlimited-Tests</h5>
          <!-- svelte-ignore a11y-invalid-attribute -->
          <a class="three" href="" on:click={() => {getPlan('Plan-B')}}>Get Plan</a>
        </div>
        <div class="status-card">
          <h4>Plan-C</h4>
          <h2>₹ 999</h2>
          <h6>Six Months</h6>
          <h5>Unlimited-Tests</h5>
          <!-- svelte-ignore a11y-invalid-attribute -->
          <a class="six" href="" on:click={() => {getPlan('Plan-C');
            swal({
  title: "Are you sure?",
  text: "Are you sure that you want to leave this page?",
  icon: "warning",
  dangerMode: true,
})
.then(willDelete => {
  if (willDelete) {
    swal("Deleted!", "Your imaginary file has been deleted!", "success");
  }
});}}>Get Plan</a>
        </div>
      </div>
      


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
{:else}
  <Test time={timer} test_Date={testDate} />
{/if}

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
  .aside {
    padding: 2.4rem 0;
    text-align: center;
    width: 26%;
    height: 100vh;
    color: #fff;
    background-image: linear-gradient(to right, #57b973, #2fa751);
    box-shadow: rgb(38, 57, 77) 0px 20px 30px -10px;
    overflow: hidden;
    position: relative;
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

  .status-cards {
    margin: 4rem 2rem;
    display: grid;
    grid-template-columns: repeat(4,1fr);
    gap: 1.4rem;
  }
  .status-cards .status-card {
    width: 100%;
    padding: 3rem 0;
    text-align: center;
    background-image: linear-gradient(to right, #57b973, #2fa751);
    border-radius: 6px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    color: #fff;
    transition: all 0.24s ease-out;
  }
  .status-cards .status-card:hover {
    transform: scale(1.04);
  }
  .status-cards .status-card:first-child {
    background: linear-gradient(to right, #d04ed6, #834d9b);
  }
  .status-cards .status-card:nth-child(2) {
    background: linear-gradient(to right, #fb8500, #fb5607);
  }
  .status-cards .status-card:nth-child(3) {
    background-color: #378b29;

    background-image: linear-gradient(to left, #378b29 0%, #35b945 74%);
  }
  .status-cards .status-card:last-child {
    background-color: #f71735;
    background-image: linear-gradient(147deg, #e62740 0%, #991a27 74%);
  }

  .status-cards .status-card h2 {
    font-size: 3rem;
    margin: 2.4rem 0;
    
  }
  .status-cards .status-card a {
    display: inline-block;
    padding: 5% 8%;
    /* background-color: #d9e4f5; */
    color: #fff;
    border: #d9e4f5 2px solid;
    border-radius: 3px;
    margin-top: 1.5rem;
    transition: all 0.16s;
  }
  .status-cards .status-card a.free:hover {
    background-color: #d9e4f5;
    color: #d04ed6;
  }
  .status-cards .status-card a.one:hover {
    background-color: #d9e4f5;
    color: #fb8500;
  }
  .status-cards .status-card a.three:hover {
    background-color: #d9e4f5;
    color: #35b945;
  }
  .status-cards .status-card a.six:hover {
    background-color: #d9e4f5;
    color: #e62740;
  }
  main {
    width: 100%;
    text-align: center;
    height: 100vh;
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
  main .test-attend {
    padding: 0.4rem 1rem;
    background-image: linear-gradient(to right, #57b973, #2fa751);
    border-radius: 4px;
    color: #fff;
    margin: 0 auto;
    display: inline-block;
    margin-bottom: 1rem;
    transition: 0.12s all ease-in;
    margin: 10px;
  }
  main .test-attend:hover {
    opacity: 0.86;
  }

  .card {
    width: 90%;
    margin: 0 auto;
    text-align: center;
    background-color: rgb(255, 255, 255);
    color: #444;
    border-radius: 6px;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    padding: 1rem 0;
  }
  button {
    border-radius: 3px;
  }
  .card img {
    width: 3rem;
    margin: 0.8rem auto;
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
    margin: 0 auto;
    display: inline-block;
    margin-bottom: 1rem;
    transition: 0.12s all ease-in;
  }
  .card a:hover {
    background-color: #2fa751;
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
  }
  @media (max-width: 760px) {
    .aside .profile-links a svg {
      display: block;
    }
    .aside .profile-links a span {
      display: none;
    }
    .status-cards {
      grid-template-columns: repeat(2,1fr);
    }
  }
  @media (max-width: 600px) {
    main {
      height: 100%;
    }
    
    .show-aside {
      width: 36%;
    }
  }
  @media (max-width: 500px) {
    .status-cards {
      grid-template-columns: 1fr;
    }
  }
</style>
