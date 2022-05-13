<script>
   import { server_URL } from "../../../config";
   import Captcha from "./Captcha.svelte"

  const obj = {
    email: "",
    password: "",
  };
  let statusMessage;
  let succesMessage='Logged in';
  const createData = async (path) => {
    console.log(obj.password);
    const response = await fetch(`${server_URL}/${path}`, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(obj),
    });
    const data = await response.json();
    statusMessage = data.message
  };
  const getCaptcha = (event) => {
    console.log(event.detail);
  }
</script>
<div class="signin">
  <div class="status-message">
    {#if statusMessage}
  <h4 style="color:{statusMessage==succesMessage?'green':'red'};" >{statusMessage}</h4>
  {#if statusMessage=='This e-mail is not verified'}
    <!-- svelte-ignore a11y-invalid-attribute -->
    <span>Click here To<a href="#"><button on:click={()=>{createData('reverification')}}>Verify</button></a></span>
  {/if}

  {/if}
  </div>
  
  <div class="signin-form">
    <form on:submit|preventDefault={() => {
      createData('login');
    }}>
      <h1 class="form-heading">Sign In</h1>

      <div class="form-floating">
        <input
          type="email"
          class="form-control"
          id="floatingInput"
          placeholder="name@example.com"
          bind:value={obj.email}
          required
        />
        <label for="floatingInput"
          >Email address
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            fill="currentColor"
            class="bi bi-envelope-fill"
            viewBox="0 0 16 16"
          >
            <path
              d="M.05 3.555A2 2 0 0 1 2 2h12a2 2 0 0 1 1.95 1.555L8 8.414.05 3.555ZM0 4.697v7.104l5.803-3.558L0 4.697ZM6.761 8.83l-6.57 4.027A2 2 0 0 0 2 14h12a2 2 0 0 0 1.808-1.144l-6.57-4.027L8 9.586l-1.239-.757Zm3.436-.586L16 11.801V4.697l-5.803 3.546Z"
            />
          </svg>
        </label>
      </div>
      <div class="form-floating">
        <input
          type="password"
          class="form-control"
          id="floatingPassword"
          placeholder="Password"
          bind:value={obj.password}
          required
        />
        <label for="floatingPassword"
          >Password
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            fill="currentColor"
            class="bi bi-key-fill"
            viewBox="0 0 16 16"
          >
            <path
              d="M3.5 11.5a3.5 3.5 0 1 1 3.163-5H14L15.5 8 14 9.5l-1-1-1 1-1-1-1 1-1-1-1 1H6.663a3.5 3.5 0 0 1-3.163 2zM2.5 9a1 1 0 1 0 0-2 1 1 0 0 0 0 2z"
            />
          </svg>
        </label>
      </div>
      <Captcha on:captcha = {getCaptcha} />
      <div class="forgot-password">
        <a href="/forgot-password">Forgot password?</a>
      </div>
      <button
          class="w-100 btn btn-lg btn-success"
          type="submit">Sign in</button
        >
      
    </form>
  </div>
</div>

<style>
  .signin {
    padding: 1.2rem 0;
  }
  .signin-form {
    width: 30%;
    margin: 3rem auto;
    text-align: center;
    background-color: rgb(234, 235, 238);
    padding:0.6rem 2rem;
    border-radius: 12px;
  }

  .signin-form .form-heading:first-child {
    margin: 1rem 0;
  }
  .form-floating {
    margin: 1rem 0;
  }
  .btn-success {
    width: 75%;
    margin: 1.2rem 0;
    background-color: #57b973;
  }
  .btn-success:hover {
    background-color: #2fa751;
  }
  .forgot-password {
    margin: .6rem 0;
  }
  label {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .status-message {
    text-align: center;
    margin-top: 1rem;
    margin-bottom: 10px;
  }
  .status-message button {
    margin-left: 0.7rem;
    padding: 5px 10px;
    border-radius: 4px;
  }
  @media (max-width: 900px) {
    .signin-form {
      width: 50%;
    }
  }
  @media (max-width: 600px) {
    .signin-form {
      width: 80%;
    }
  }
</style>
