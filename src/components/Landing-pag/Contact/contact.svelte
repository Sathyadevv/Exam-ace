<section id="contact" class="contact">
  <div class="container" data-aos="fade-up">
    <div class="section-title">
      <h2>Contact</h2>
      <div class="underline" />
    </div>

    <div class="row mt-5">
      <div class="col-lg-4">
        <div class="info">
          <div class="address">
            <i class="bi bi-geo-alt" />
            <h4>Location:</h4>
            <p>No,x,XYZ street,country.</p>
          </div>

          <div class="email">
            <i class="bi bi-envelope" />
            <h4>Email:</h4>
            <p>info@example.com</p>
          </div>

          <div class="phone">
            <i class="bi bi-phone" />
            <h4>Call:</h4>
            <p>+1 5589 55488 55s</p>
          </div>
        </div>
      </div>

      <div class="col-lg-8 mt-5 mt-lg-0">
        <!-- svelte-ignore a11y-no-redundant-roles -->
        <form
          action="forms/contact.php"
          method="post"
          role="form"
          class="php-email-form"
        >
          <div class="row">
            <div class="col-md-6 form-group">
              <input
                type="text"
                name="name"
                class="form-control"
                id="name"
                placeholder="Your Name"
                required
              />
            </div>
            <div class="col-md-6 form-group mt-3 mt-md-0">
              <input
                type="email"
                class="form-control"
                name="email"
                id="email"
                placeholder="Your Email"
                required
              />
            </div>
          </div>
          <div class="form-group mt-3">
            <input
              type="text"
              class="form-control"
              name="subject"
              id="subject"
              placeholder="Subject"
              required
            />
          </div>
          <div class="form-group mt-3">
            <textarea
              class="form-control"
              name="message"
              rows="5"
              placeholder="Message"
              required
            />
          </div>
          <div class="my-3">
            <div class="loading">Loading</div>
            <div class="error-message" />
            <div class="sent-message">
              Your message has been sent. Thank you!
            </div>
          </div>
          <div class="text-center" id="send">
            <button type="submit">Send Message</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</section>

<style>
  #contact {
    margin: 2rem 0;
  }
  .contact .info {
    width: 100%;
    background: #fff;
  }
  .contact .info i {
    font-size: 20px;
    background: #57b973;
    color: #fff;
    float: left;
    width: 44px;
    height: 44px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 4px;
    transition: all 0.3s ease-in-out;
  }
  .contact .info h4 {
    padding: 0 0 0 60px;
    font-size: 22px;
    font-weight: 600;
    margin-bottom: 5px;
    color: #151515;
  }
  .contact .info p {
    padding: 0 0 0 60px;
    margin-bottom: 0;
    font-size: 14px;
    color: #484848;
  }
  .section-title {
    text-align: center;
  }
  .section-title .underline {
    margin: 1rem auto;
    height: 4px;
    width: 50px;
    background-color: #333;
    border-radius: 3px;
  }
  .contact .info .email,
  .contact .info .phone {
    margin-top: 40px;
  }
  .contact .php-email-form {
    width: 100%;
    background: #fff;
  }
  .contact .php-email-form .form-group {
    padding-bottom: 8px;
  }
  .contact .php-email-form .error-message {
    display: none;
    color: #fff;
    background: #ed3c0d;
    text-align: left;
    padding: 15px;
    font-weight: 600;
  }

  .contact .php-email-form .sent-message {
    display: none;
    color: #fff;
    background: #18d26e;
    text-align: center;
    padding: 15px;
    font-weight: 600;
  }
  .contact .php-email-form .loading {
    display: none;
    background: #fff;
    text-align: center;
    padding: 15px;
  }
  .contact .php-email-form .loading:before {
    content: "";
    display: inline-block;
    border-radius: 50%;
    width: 24px;
    height: 24px;
    margin: 0 10px -6px 0;
    border: 3px solid #18d26e;
    border-top-color: #eee;
    -webkit-animation: animate-loading 1s linear infinite;
    animation: animate-loading 1s linear infinite;
  }
  .contact .php-email-form input,
  .contact .php-email-form textarea {
    border-radius: 0;
    box-shadow: none;
    font-size: 14px;
    border-radius: 4px;
  }
  .contact .php-email-form input:focus,
  .contact .php-email-form textarea:focus {
    border-color: #57b973;
  }
  .contact .php-email-form input {
    height: 44px;
  }
  .contact .php-email-form textarea {
    padding: 10px 12px;
  }
  .contact .php-email-form button[type="submit"] {
    background: #57b973;
    border: 0;
    padding: 10px 24px;
    color: #fff;
    transition: 0.2s;
    border-radius: 4px;
  }
  .contact .php-email-form button[type="submit"]:hover {
    opacity: 0.86;
  }
</style>
