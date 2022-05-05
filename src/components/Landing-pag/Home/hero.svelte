<script>
    

</script>

<div class="hero">
    <!-- svelte-ignore a11y-img-redundant-alt -->
    <img class='hero-img' src='../assets/images/pexels-pixabay-356065.jpg' alt="hero-image">
    <div class="carousals">
        <div id="carouselExampleSlidesOnly" class="carousel slide" data-bs-ride="carousel">
            <div class="carousel-inner">
              <div class="carousel-item active">
                <!-- svelte-ignore a11y-img-redundant-alt -->
                <!-- svelte-ignore a11y-invalid-attribute -->
                <a href="#">                <img src="../assets/images/Frame 1.png" class="d-block w-100" alt="carousal-image">
                </a>
              </div>
              <div class="carousel-item">
                <!-- svelte-ignore a11y-img-redundant-alt -->
                <!-- svelte-ignore a11y-invalid-attribute -->
                <a href="#">                <img src="../assets/images/Frame 3.png" class="d-block w-100" alt="carousal-image">
                </a>
              </div>
              
            </div>
          </div>
    </div>
</div>

<style>
    .hero {
        position: relative;
    }
    .hero-img {
      height: 586px;
      width: 100%;
      filter: brightness(60%) blur(3px);
  }
  .hero .carousals {
      width: 70%;
      background-color: #57B973;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%,-50%);
  }
  @media (max-width:528px) {
    .hero .carousals {
      width: 92%;
    }
  }
</style>