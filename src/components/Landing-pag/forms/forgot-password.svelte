<script>
    import { server_URL } from "../../../config";
    import Captcha from "./Captcha.svelte"
   const obj = {
     email: "",
   };
    let statusMessage;
    let succesMessage='Please check your e-mail for password recovery';
   const createData = async () => {
     const response = await fetch(`${server_URL}/resetpassword`, {
       method: "POST",
       headers: {
         "Content-Type": "application/json",
       },
       body: JSON.stringify(obj),
     });
     const data = await response.json();
    statusMessage = data.message
   };
 </script>
 <div class="signin">
  {#if statusMessage}
  <h4 style="color:{statusMessage==succesMessage?'green':'red'};" class="status-message">{statusMessage}</h4>

  {/if}
   <div class="signin-form">
     <form on:submit|preventDefault={() => {
       createData();
     }}>
       <h3 class="form-heading">Forgot Password</h3>
 
       <div class="form-floating">
         <input
           type="email"
           class="form-control"
           id="floatingInput"
           placeholder="name@example.com"
           bind:value={obj.email}
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
      
       <button
           class="w-100 btn btn-lg btn-success"
           type="submit">Get Password</button
         >
       
     </form>
   </div>
 </div>
 <style>
   .signin {
     padding: 4rem 0;
   }
   .signin-form {
     width: 30%;
     margin: 3rem auto;
     text-align: center;
     background-color: rgb(234, 235, 238);
     padding: 2rem 2rem;
     padding-bottom: 4rem;
     border-radius: 12px;
   }
 
   .signin-form .form-heading {
     margin: 1.4rem 0;
     margin-bottom: 4rem;
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
   
   label {
     width: 100%;
     display: flex;
     align-items: center;
     justify-content: space-between;
   }
   .status-message {
    text-align: center;
    margin-top: 1rem;
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
 