<div class="signin">
  <div class="signin-form">
    <form>
      <h1 class="form-heading">Sign In</h1>

      <div class="form-floating">
        <input
          type="email"
          class="form-control"
          id="floatingInput"
          placeholder="name@example.com"
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
      <div class="forget-password">
        <a href="#!">Forgot password?</a>
      </div>
      <a href="/app">
        <button
          on:click={() => {
            formVal = false;
          }}
          class="w-100 btn btn-lg btn-success"
          type="submit">Sign in</button
        >
      </a>
    </form>
  </div>
</div>

<style>
  .signin {
    padding: 2rem 0;
  }
  .signin-form {
    width: 30%;
    margin: 3rem auto;
    text-align: center;
    background-color: rgb(234, 235, 238);
    padding: 2rem;
    border-radius: 12px;
  }

  .signin-form .form-heading {
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
  .forget-password {
    margin: 1.6rem 0;
  }
  label {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
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
