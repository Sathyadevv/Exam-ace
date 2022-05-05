<script>
  import { server_URL } from "../../../url";
  const obj = {
    name: "",
    e_mail: "",
    password: "",
    date_of_birth: "",
    gender: "",
    description: "",
  };

  const getGender = () => {
    let genders = document.querySelectorAll(".gender");
    genders.forEach((gend) => {
      if (gend.checked) {
        obj.gender = gend.value;
      }
    });
  };
  const createData = async () => {
    const response = await fetch(`${server_URL}signup`, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(obj),
    });
    const data = response.json();
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
        />
        <label for="floatingInput">Name</label>
      </div>
      <div class="form-floating">
        <input
          type="date"
          class="form-control"
          id="floatingInput"
          placeholder="false"
          bind:value={obj.date_of_birth}
        />
        <label for="floatingInput">Date-of-Birth</label>
      </div>

      <div class="form-floating">
        <input
          type="email"
          class="form-control"
          id="floatingInput"
          placeholder="name@example.com"
          bind:value={obj.e_mail}
        />
        <label for="floatingInput">Email address</label>
      </div>
      <div class="form-floating">
        <input
          type="password"
          class="form-control"
          id="floatingPassword"
          placeholder="Password"
          bind:value={obj.password}
        />
        <label for="floatingPassword">Password</label>
      </div>
      <div class="form-floating">
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
      </div>

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
    margin: 0.6rem auto;
    text-align: center;
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

  .signin-form .form-heading {
    margin: 2rem 0;
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
    opacity: 0.92;
  }
  .gender-cont {
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
  }
</style>
