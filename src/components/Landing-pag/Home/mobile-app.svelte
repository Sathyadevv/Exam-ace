<div class="mobile-app">
  <div class="containerr">
    <div class="flex">
      <div>
        <img src="../assets/images/mobile.png" alt="" />
      </div>
      <div class="app-text">
        <h3>ACCESS ANYTIME YOU WANT</h3>
        <!-- svelte-ignore missing-declaration -->
        <p>
          Get Access To Exam <span style="color: #57B973;">App</span> from your Pocket.
        </p>
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a href="#" class="gplay-btn">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            x="0px"
            y="0px"
            width="32"
            height="32"
            viewBox="0 0 48 48"
            style=" fill:#000000;"
            ><path
              fill="#4db6ac"
              d="M7.705,4.043C7.292,4.15,7,4.507,7,5.121c0,1.802,0,18.795,0,18.795S7,42.28,7,43.091c0,0.446,0.197,0.745,0.5,0.856l20.181-20.064L7.705,4.043z"
            /><path
              fill="#dce775"
              d="M33.237,18.36l-8.307-4.796c0,0-15.245-8.803-16.141-9.32C8.401,4.02,8.019,3.961,7.705,4.043l19.977,19.84L33.237,18.36z"
            /><path
              fill="#d32f2f"
              d="M8.417,43.802c0.532-0.308,15.284-8.825,24.865-14.357l-5.601-5.562L7.5,43.947C7.748,44.038,8.066,44.004,8.417,43.802z"
            /><path
              fill="#fbc02d"
              d="M41.398,23.071c-0.796-0.429-8.1-4.676-8.1-4.676l-0.061-0.035l-5.556,5.523l5.601,5.562c4.432-2.559,7.761-4.48,8.059-4.653C42.285,24.248,42.194,23.5,41.398,23.071z"
            /></svg
          > Get it on GOOGLE-PLAY
        </a>
      </div>
    </div>
  </div>
</div>

<style>
  .mobile-app {
    padding: 3rem 0;
  }
  .containerr {
    max-width: 60%;
    margin: 0 auto;
  }
  .containerr .flex {
    margin: 0 auto;
    display: flex;
    align-items: center;
  }
  .app-text h3 {
    color: #444;
    font-size: 1.7rem;
    letter-spacing: 1.2px;
  }
  .app-text p {
    margin: 1.8rem 0;
    font-size: 1.1rem;
  }
  .app-text a {
    cursor: pointer;
    border: rgb(182, 173, 173) 2px solid;
    padding: 6px 14px;
    text-decoration: none;
    color: #555;
    border-radius: 6px;
    display: inline-block;
    font-size: 12px;
    font-weight: 700;
    background-color: rgb(225, 226, 230);
    transition: all 0.16s ease-out;
  }
  .app-text a:hover {
    box-shadow: rgba(0, 0, 0, 0.35) 0px 3px 15px;
  }
  @media (max-width: 800px) {
    .containerr {
      max-width: 80%;
    }
    .app-text h3 {
      font-size: 1.4rem;
    }
    .app-text p {
      font-size: 0.9rem;
    }
  }
  @media (max-width: 560px) {
    .containerr {
      max-width: 96%;
    }
    .app-text p {
      margin: 1.2rem 0;
    }
    .app-text a {
      padding: 4px 10px;
      font-size: 10px;
    }
  }
</style>
