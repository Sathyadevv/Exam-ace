<script>
  import { server_URL } from "../../../config";
  const obj = {
    name: "",
    email: "",
    password: "",
  };

  // const getGender = () => {
  //   let genders = document.querySelectorAll(".gender");
  //   genders.forEach((gend) => {
  //     if (gend.checked) {
  //       obj.gender = gend.value;
  //     }
  //   });
  // };
  const createData = async () => {
    const response = await fetch(`${server_URL}/signup`, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(obj),
    });
    const data = await response.json();
    console.log(data);
  };
</script>

<div class="signin">
  <div class="signin-form">
    <form
      on:submit|preventDefault={() => {
        createData();
      }}
    >
      <h1 class="form-heading">Sign Up</h1>

      <div class="form-floating">
        <input
          type="text"
          class="form-control"
          id="floatingInput"
          placeholder="name@example.com"
          bind:value={obj.name}
          required
        />
        <label for="floatingInput"
          >Name
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            fill="currentColor"
            class="bi bi-person-fill"
            viewBox="0 0 16 16"
          >
            <path
              d="M3 14s-1 0-1-1 1-4 6-4 6 3 6 4-1 1-1 1H3zm5-6a3 3 0 1 0 0-6 3 3 0 0 0 0 6z"
            />
          </svg>
        </label>
      </div>
      <!-- <div class="form-floating">
        <input
          type="date"
          class="form-control"
          id="floatingInput"
          placeholder="false"
          bind:value={obj.date_of_birth}
        />
        <label for="floatingInput">Date-of-Birth</label>
      </div> -->

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
      <!-- <div class="form-floating">
        <input
          type="text"
          class="form-control"
          id="floatingInput"
          placeholder="Description"
          bind:value={obj.description}
        />
        <label for="floatingPassword">Description</label>
      </div>
      <div class="gender-cont">
        <label for="gender" class="gender-label"> Gender</label>
        <div class="gender-div">
          <span
            ><input
              class="gender"
              on:click={() => {
                getGender();
              }}
              type="radio"
              name="gender"
              value="male"
            /> Male</span
          > 
          

          <span
            ><input
              class="gender"
              on:click={() => {
                getGender();
              }}
              type="radio"
              name="gender"
              value="female"
            /> Female</span
          >
          <span
            ><input
              class="gender"
              on:click={() => {
                getGender();
              }}
              type="radio"
              name="gender"
              value="other"
            /> Other</span
          >
        </div>
      </div> -->

      <button class="w-100 btn btn-lg btn-success" type="submit"
        >Register</button
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
    padding: 2rem;
    border-radius: 12px;
  }

  .signin-form .form-heading {
    margin: 1rem 0;
  }
  .form-floating {
    margin: 14px 0;
  }
  .btn-success {
    width: 75%;
    margin: 1.2rem 0;
    background-color: #57b973;
  }
  .btn-success:hover {
    background-color: #2fa751;
  }
  label {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  /* .gender-cont {
    display: flex;
    align-items: center;
    justify-content: space-around;
    margin: 1rem 0;
  }
  input[type="radio"] {
    margin-left: 6px;
    cursor: pointer;
  }
  @media (max-width: 500px) {
    .gender-div {
      display: flex;
      flex-direction: column;
    }
  } */
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
