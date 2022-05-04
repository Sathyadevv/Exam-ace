<script>
    import {slide,fade} from 'svelte/transition'
     let val = true;
     const toggle = ()=> {val=!val}
</script>
<div>
    <nav>
        <div class="containerr">
            <div class="nav-bar">
                <div class="logo">
                    <h2><a href='/'>Exam<span style="color: #57B973;font-weight:bold">App</span></a></h2>
                        
                </div>
                <div class="nav-links">
                    <a href='/' class="nav-link">HOME</a>
                    <a href='/' class="nav-link">COURSES</a>
                    <a href='/about' class="nav-link">ABOUT</a>
                    <a href='/contact' class="nav-link">CONTACT</a>
                </div>
                <div class='nav-end'>
                    <a class="btn-login" href='/sign-in'>Log In</a>
                    <a class="btn-signup" href='/sign-up'>Sign Up</a>
                    <div class="hamburger-menu" on:click={toggle}>
                        {#if val}
                        <svg xmlns="http://www.w3.org/2000/svg" width="36" height="36"  fill="#57B973" class="bi bi-list" viewBox="0 0 16 16">
                            <path fill-rule="evenodd" d="M2.5 12a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z"/>
                          </svg>
    
    
          
                        {:else}
                        <svg xmlns="http://www.w3.org/2000/svg" width="34" height="34" fill="#57B973" class="bi bi-x" viewBox="0 0 16 16">
                            <path d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708z"/>
                          </svg>
                        {/if}
                    
                    </div>
                </div>
                
            </div>
            
                {#if !val}
                <div class="responsive">
                    <div class="r-links">
                        <div class='flex'>
                            <a href='/' on:click={toggle} class="r-link">Home</a>
                            <a href='/about' on:click={toggle} class="r-link">About</a>
                            <a href='/' on:click={toggle} class="r-link">Courses</a>
                            <a href='/contact' on:click={toggle} class="r-link">Contact</a>
                        </div>
                        
    
                    </div>
                </div>
                
                {/if}
                
                
        </div>
    </nav>
    
    
</div>

<style>
    nav {
        position: fixed;
        top: 0;
        right: 0;
        left: 0;
        padding: 4px 0;
        z-index: 5;
        background-color: #fff;
        box-shadow: rgba(50, 50, 93, 0.25) 0px 6px 12px -2px, rgba(0, 0, 0, 0.3) 0px 3px 7px -3px;
    }
    a {
        display: inline-block;
        text-decoration: none;
    }
    .containerr {
        width: 86%;
        margin: 0 auto;
    }
    .nav-bar {
        height: 5rem;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .nav-bar .logo {
        font-size: 1.6rem;
    }
    .nav-bar a {
        color: #333;
    }
    .nav-bar .nav-links {
        margin-left: 2.4rem;
    }
    .nav-bar .nav-links .nav-link {
        font-weight: 700;
        font-size: 0.9rem;
        margin-left: 1.4rem;
        border-bottom: 2px solid transparent;
        padding: 5px 0;
        transition: all 0.2s ease-in;
        margin-top: 9px;
        letter-spacing: 1px;
    }
    .nav-bar .nav-links .nav-link:hover {
        color: #57B973;
        border-bottom: #57B973 2px solid;
    }
    .nav-bar .btn-login,
    .nav-bar .btn-signup {
        font-size: 14px;
        padding: 3px 8px;
        border: 1px solid #777;
        border-radius: 6px;
        transition: all 0.2s ease-in-out;
        margin: 0 0.6rem;
    }
    .nav-bar .btn-login:hover,
    .nav-bar .btn-signup:hover {
        background-color: #57B973;
        color: #fff;
    }
    .hamburger-menu {
        cursor: pointer;
        border-radius: 3px;
        overflow: hidden;
        display: none;

    }
    .responsive {
        display: none;
    }
    svg {
        width: 100%;
    }
    @media (max-width:960px) {

        .nav-bar .nav-links {
        margin:0.6rem;
    }  }
    @media (max-width:780px) {
        
        .flex {
            display: flex;
            flex-direction: column;
        }
        .nav-bar .nav-links {
        margin-left: 1.8rem;
    }
        .hamburger-menu {
            display: block;
        }
        .nav-bar .nav-links{
            display: none;
        }
        .nav-end {
            display: flex;
        }
        .responsive {
            display: block;
        }
        .responsive .r-links {
            height: auto;
            text-align: center;
            padding-top: 2rem;
        }
        .responsive .r-links .r-link {
            margin: 1.8rem 0;
            font-size: 1.7rem;
            cursor:pointer;
            transition: all 0.2s ease-in;
            color: #333;
        }
        .responsive .r-links .r-link:hover {
            color: #57B973;
        }

    }
    @media (max-width:528px) {
        nav {
            padding: 2px 0;
        }
        .containerr {
            width: 96%;
        }
    }
</style>