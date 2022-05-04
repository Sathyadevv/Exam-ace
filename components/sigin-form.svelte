<script>
	export let formVal
</script>
<div class="signin">
	<div class="signin-form">
	    <form>
			<h1 class="form-heading">Sign In</h1>
		
			
		
			<div class="form-floating">
			  <input type="email" class="form-control" id="floatingInput" placeholder="name@example.com">
			  <label for="floatingInput">Email address</label>
			</div>
			<div class="form-floating">
			  <input type="password" class="form-control" id="floatingPassword" placeholder="Password">
			  <label for="floatingPassword">Password</label>
			</div>
			<div class="forget-password">
				<a href="#!">Forgot password?</a>		
	        </div>
		    <a href="/app">
				<button on:click={()=>{formVal=false}} class="w-100 btn btn-lg btn-success" type="submit">Sign in</button>
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
  }
 
  @media (max-width:900px) {
	  .signin-form {
		  width: 50%;
	  }
  }
  @media (max-width:600px) {
	  .signin-form {
		  width: 80%;
	  }
  }

  .signin-form .form-heading {
	  margin: 2.4rem 0;
  }
  .form-floating {
	  margin: 1.4rem 0;
  }
  .btn-success {
	  width: 75%;
	  margin: 1.2rem 0;
	  background-color: #57B973;
  }
  .btn-success:hover {
	  opacity: 0.92;
  }
  .forget-password {
	  margin: 1.6rem 0;
  }
</style>


