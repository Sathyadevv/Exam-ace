<div class="faculty">
    <div class="containerr">
        <h2 class='heading'>Lorem ipsum dolor sit amet.</h2>
        <div class="faculty-sub">
            <div class="faculty-sub-sub">
                <div class='features'>
                    <div class="feature">
                        <span><img class="img-responsive" src="../assets/icons/feature-4.png" alt=""></span>
                            <p>Lorem ipsum dolor sit amet.</p>
                    </div>
                    
                    <div class="feature">
                        <span><img class="img-responsive" src="../assets/icons/doubt-clearification.png" alt=""></span>
                            <p>Lorem ipsum dolor sit amet.</p>
                    </div>
                    <div class="feature">
                        <span><img class="img-responsive" src="../assets/icons/feature-3.png" alt=""></span>
                            <p>Lorem ipsum dolor sit amet consectetur.</p>
                    </div>
                    <div class="feature">
                        <span><img class="img-responsive" src="../assets/icons/feature-6.png" alt=""></span>
                        <p>Lorem ipsum dolor sit.</p>
                    </div>   
                    
                    <div class="feature">
                        <span><img class="img-responsive" src="../assets/icons/feature-5.png" alt=""></span>
                            <p>Lorem ipsum dolor sit amet.</p>
                    </div>
                    <div class="feature">
                        <span><img class="img-responsive" src="../assets/icons/recorded-lectures.png" alt=""></span>
                            <p>Lorem ipsum dolor sit amet consectetur.</p>
                    </div>
                      
                </div>
            </div>
            
            <!-- <div class='faculty-img'>
                 svelte-ignore a11y-img-redundant-alt 
                <img src="../assets/images/faculty.png" alt="faculty-image">
            </div> -->
        </div>
        
                
            
            
        
    </div>
</div>



<style>
    img {
        max-width: 100%;
    }
    
    .faculty {
        height: 100vh;
        margin: 3.6rem auto;
        background-image: linear-gradient(rgba(0, 0, 0, 0.8),
                       rgba(0, 0, 0, 0.8)), url('../assets/images/pexels-karolina-grabowska-4021779.jpg');
        background-repeat: no-repeat;
        background-position: top;
        background-size: cover;
        text-align: center;
        padding: 4rem 0;
        color: #fff; 
    }
    .containerr {
        width: 80%;
        margin: 0 auto;
    }
    .faculty .heading {
        font-size: 2.2rem;
        letter-spacing: 1.2px;
    }
    .faculty-sub {
        margin: 4rem auto;
    }
    .faculty-sub .faculty-sub-sub {
        max-width: 70%;
        margin: 0 auto;
    }
    .faculty-sub .features {
        margin: 0 auto;
        display: grid;
        grid-template-columns: repeat(3,1fr);
    }
    .faculty-sub .features .feature {
        padding: 1rem 1.6rem;
    }
    .faculty-sub .features .feature  p {
        padding-top: 6px;
    }
    .faculty-sub .features .feature:nth-of-type(odd) {
      background-color: #57B973;
    }
    .faculty-sub .features .feature:nth-of-type(even) {
      background-color: #41b461;
    }
    /* .faculty-img {
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-left: 3rem;
    } */
    .img-responsive {
        filter: invert(1%) sepia(1%) saturate(1%) hue-rotate(1deg) brightness(1000%) contrast(80%);
    }
    @media (max-width:800px) {
        
        .faculty {
            height: auto;
        }.containerr {
            width: 88%;
        } }
    @media (max-width:660px) {
        
        .faculty {
            height: auto;
        }
    .containerr {
        max-width: 92%;
    }
    .faculty-sub .faculty-sub-sub {
        max-width: 94%;
    }
    .faculty-sub {
        margin: 3rem auto;
    }
        .faculty-sub .features {
        grid-template-columns: repeat(2,1fr);
    }
    .faculty-sub .features .feature:nth-of-type(odd) {
      background-color: #41b461;
    }
    .faculty-sub .features .feature:nth-child(1) {
      background-color: #57B973;
    }
    .faculty-sub .features .feature:nth-child(4) {
      background-color: #57B973;
    }
    .faculty-sub .features .feature:nth-child(5) {
      background-color: #57B973;
    }
    
    
    }
    @media (max-width:480px) {
        
        .faculty {
            height: auto;
            padding: 2.8rem 0;
        }
        .faculty-sub .faculty-sub-sub {
        max-width: 100%;
    }
        .faculty-sub {
            margin: 2rem auto;
        }
        }

</style>