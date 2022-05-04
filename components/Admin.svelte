<script>
	import Test from './test.svelte'
	import Chart from './chart.svelte'


    let val=true;
    let val2=true;
    let test_catgry = '';
    let test_arr = [{image:'../assets/icons/icons8-medical-64.png',exam:'NEET'},{image:'../assets/icons/icons8-chemistry-64.png',exam:'JAM'},{image:'../assets/icons/icons8-engineering-64.png',exam:'JEE'}]
    let showTimer = true;
    let timer = 0;
    let testDate;
    let hamVal = true;

    let toggle = () => {
        hamVal=!hamVal;
    }
    
</script>


    {#if val}
    <div class="body">
        <a href="" class="hamburger-menu" on:click={toggle}>
            {#if hamVal}
            <svg xmlns="http://www.w3.org/2000/svg" width="36" height="36"  fill="#57B973" class="bi bi-list" viewBox="0 0 16 16">
                <path fill-rule="evenodd" d="M2.5 12a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z"/>
              </svg>

            {/if}

        </a>    
        
            
            
        
        
      <div class="aside {hamVal?'':'show-aside'}">
        {#if !hamVal}
        <a href="" class="close" on:click={toggle}>
            <svg xmlns="http://www.w3.org/2000/svg" width="34" height="34" fill="#57B973" class="bi bi-x" viewBox="0 0 16 16">
                <path d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708z"/>
              </svg>
        </a>
        {/if}
        
        <div class="main">
          <img src="../assets/icons/images.jpeg" alt="" class="profile-image">
          <h3 class='profile-name'>Admin name</h3>
        </div>
        <div class="profile-links">
          <a href="">
              <div class="i">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-house-door-fill" viewBox="0 0 16 16">
                    <path d="M6.5 14.5v-3.505c0-.245.25-.495.5-.495h2c.25 0 .5.25.5.5v3.5a.5.5 0 0 0 .5.5h4a.5.5 0 0 0 .5-.5v-7a.5.5 0 0 0-.146-.354L13 5.793V2.5a.5.5 0 0 0-.5-.5h-1a.5.5 0 0 0-.5.5v1.293L8.354 1.146a.5.5 0 0 0-.708 0l-6 6A.5.5 0 0 0 1.5 7.5v7a.5.5 0 0 0 .5.5h4a.5.5 0 0 0 .5-.5z"/>
                  </svg>
                  <span>Home</span>
              </div>
            </a>
          <a href="">
              <div class="i">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-alarm-fill" viewBox="0 0 16 16">
                    <path d="M6 .5a.5.5 0 0 1 .5-.5h3a.5.5 0 0 1 0 1H9v1.07a7.001 7.001 0 0 1 3.274 12.474l.601.602a.5.5 0 0 1-.707.708l-.746-.746A6.97 6.97 0 0 1 8 16a6.97 6.97 0 0 1-3.422-.892l-.746.746a.5.5 0 0 1-.707-.708l.602-.602A7.001 7.001 0 0 1 7 2.07V1h-.5A.5.5 0 0 1 6 .5zm2.5 5a.5.5 0 0 0-1 0v3.362l-1.429 2.38a.5.5 0 1 0 .858.515l1.5-2.5A.5.5 0 0 0 8.5 9V5.5zM.86 5.387A2.5 2.5 0 1 1 4.387 1.86 8.035 8.035 0 0 0 .86 5.387zM11.613 1.86a2.5 2.5 0 1 1 3.527 3.527 8.035 8.035 0 0 0-3.527-3.527z"/>
                  </svg>
                  <span>Recent</span>
              </div>
            </a>
          <a href="">
              <div class="i">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-bar-chart-fill" viewBox="0 0 16 16">
                    <path d="M1 11a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v3a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1v-3zm5-4a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v7a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1V7zm5-5a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V2z"/>
                  </svg>
                  <span>Chart</span>
              </div>
            </a>
          <a href="">
              <div class="i">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-gear-fill" viewBox="0 0 16 16">
                    <path d="M9.405 1.05c-.413-1.4-2.397-1.4-2.81 0l-.1.34a1.464 1.464 0 0 1-2.105.872l-.31-.17c-1.283-.698-2.686.705-1.987 1.987l.169.311c.446.82.023 1.841-.872 2.105l-.34.1c-1.4.413-1.4 2.397 0 2.81l.34.1a1.464 1.464 0 0 1 .872 2.105l-.17.31c-.698 1.283.705 2.686 1.987 1.987l.311-.169a1.464 1.464 0 0 1 2.105.872l.1.34c.413 1.4 2.397 1.4 2.81 0l.1-.34a1.464 1.464 0 0 1 2.105-.872l.31.17c1.283.698 2.686-.705 1.987-1.987l-.169-.311a1.464 1.464 0 0 1 .872-2.105l.34-.1c1.4-.413 1.4-2.397 0-2.81l-.34-.1a1.464 1.464 0 0 1-.872-2.105l.17-.31c.698-1.283-.705-2.686-1.987-1.987l-.311.169a1.464 1.464 0 0 1-2.105-.872l-.1-.34zM8 10.93a2.929 2.929 0 1 1 0-5.86 2.929 2.929 0 0 1 0 5.858z"/>
                  </svg>
                  <span>Settings</span>
              </div>
            </a>
          <a href="">
              <div class="i">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-door-open-fill" viewBox="0 0 16 16">
                    <path d="M1.5 15a.5.5 0 0 0 0 1h13a.5.5 0 0 0 0-1H13V2.5A1.5 1.5 0 0 0 11.5 1H11V.5a.5.5 0 0 0-.57-.495l-7 1A.5.5 0 0 0 3 1.5V15H1.5zM11 2h.5a.5.5 0 0 1 .5.5V15h-1V2zm-2.5 8c-.276 0-.5-.448-.5-1s.224-1 .5-1 .5.448.5 1-.224 1-.5 1z"/>
                  </svg>
                  <span>Log-out</span>
              </div>
            </a>
        </div>
      </div>
      <main>
        
          <h1>Welcome Admin</h1>
          
            <h3>Attend TEST</h3>
            {#if val2}
            <a href="" class="test-attend" on:click={()=>{val2=false;test_catgry=0;}}>
                NEET
            </a>
            <a href="" class="test-attend" on:click={()=>{val2=false;test_catgry=1;}}>
                JAM
            </a>
            <a href="" class="test-attend" on:click={()=>{val2=false;test_catgry=2;}}>
                JEE
            </a>
            {:else}
            <div class="test-card">
                <div class="card">
                   <h3>{test_arr[test_catgry].exam}</h3>
                
                   <button class="timer-on" on:click={()=>{showTimer=!showTimer;timer=0.5;
                    if(showTimer){timer=0;}}}>Timer-{showTimer?'ON':'OFF'}</button>
             
                   {#if !showTimer}
                   <div class="timer-cont">
                     <button class="minus" on:click={()=>{if(timer)timer=timer-0.5}}>-</button>
                     <button class="timer">{timer} hr</button>
                     <button class="plus" on:click={()=>{if(timer<4)timer=timer+0.5}}>+</button>
                   </div>
                   {/if}
                   <!-- svelte-ignore a11y-img-redundant-alt -->
                   <img src={test_arr[test_catgry].image} alt="test-category-image">
                   
                   <a on:click={()=>{val=false;testDate=new Date().toLocaleString([], { hour12: true});}} href="">Start</a>
                </div>
            </div>
            {/if}
         
        
          
         
          <div class="status-cards">
            <div class="status-card">
              <h4>Total-tests</h4>
              <h2>234</h2>
              <a href="">Show-more</a>
            </div>
            <div class="status-card">
              <h4>Above-Avg</h4>
              <h2>156</h2>
              <a href="">Show-more</a>
            </div>
            <div class="status-card">
              <h4>Below-Avg</h4>
              <h2>78</h2>
              <a href="">Show-more</a>
            </div>
            
          </div>


          <a class="notification" href=""><svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-bell-fill" viewBox="0 0 16 16">
            <path d="M8 16a2 2 0 0 0 2-2H6a2 2 0 0 0 2 2zm.995-14.901a1 1 0 1 0-1.99 0A5.002 5.002 0 0 0 3 6c0 1.098-.5 6-2 7h14c-1.5-1-2-5.902-2-7 0-2.42-1.72-4.44-4.005-4.901z"/>
          </svg></a>
          
      
      </main>	
    </div>
   
	{:else}    
    <Chart />
    <Test time={timer} test_Date={testDate} />
    {/if}




<style>
  
  img {
    max-width: 100%;
    height: auto;
  }
  a {
    text-decoration: none;
  }
  .body {
    display: flex;
    margin-top: -4rem;
    padding: 0;
  }
  .aside {
    padding: 2.4rem 0;
    text-align: center;
    width: 26%;
    height: 100vh;
    color: #fff;
    background-image: linear-gradient(to right, #57B973, #2fa751);
    box-shadow: rgb(204, 219, 232) 3px 3px 6px 0px inset, rgba(255, 255, 255, 0.5) -3px -3px 6px 1px inset;
    overflow: hidden;
    position: relative;
  }
  .aside .main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1.2rem;
  }
  .aside .profile-image {
    width: 2.6rem;
    height: 3rem;
    border-radius: 50%;
  }
  .aside .profile-links {
    display: flex;
    flex-direction: column;
    width: 100%;
    margin: 1.4rem auto;
  }
  .aside .profile-links a {
      width: 100%;
    text-decoration: none;
    color: #fff;
    font-weight: 700;
    font-size: 1.2rem;
    padding: 1.2rem 0;
    transition: 0.1s all ease-in;
    display: flex;
    text-align: left;
    padding-left: 20%;
    margin: 0;
   
  }
  .aside .profile-links a .i{
      display: flex;
      align-items: center;
      gap: 2.4rem;


  }
  /* .aside .profile-links a span {
      text-align: center;
      padding: 0 3rem;
  } */
  .aside .profile-links a:hover {
    background-color: #2fa751;
  }

  .status-cards {
    margin: 2rem auto;
    display: flex;
    justify-content: space-around;
    gap: 2rem;
  }
  .status-cards .status-card {
      width: 100%;
      padding: 1rem 0;
    text-align: center;
    background-image: linear-gradient(to right, #57B973, #2fa751);
    border-radius: 6px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    color: #fff;
  }
  .status-cards .status-card:first-child {
    background: linear-gradient(to right, #d04ed6, #834d9b);
  }
  .status-cards .status-card:nth-child(2) {
    background-color: #378b29;

background-image: linear-gradient(to left, #378b29 0%, #35b945 74%);

  }
  .status-cards .status-card:last-child {
    background-color: #f71735;
background-image: linear-gradient(147deg, #e62740 0%, #991a27 74%);
  }


  .status-cards .status-card h2 {
    margin: 1.4rem 0;
  }
  .status-cards .status-card a {
    color: #d9e4f5;
  }
  .status-cards .status-card a:hover {
    color: #fff;
  }
    main {
      width: 100%;
        text-align: center;
        height: 100vh;
        padding: 0 2rem;
        background-color: #d9e4f5;
        background-image: linear-gradient(315deg, #d9e4f5 0%, #f5e3e6 74%);
        
    }
    main h1 {
        margin-top: 1rem;
    }
    main h3 {
        margin: 1rem;
    }
    main .test-attend {
        
        padding: 0.4rem 1rem;
        background-image: linear-gradient(to right, #57B973, #2fa751);
      border-radius: 4px;
      color: #fff;
      margin: 0 auto;
      display: inline-block;
      margin-bottom: 1rem;
      transition: 0.12s all ease-in;
      margin: 10px;
    }
    main .test-attend:hover {
      opacity: 0.86;
    }
    
    .card {
      width: 90%;
      margin: 0 auto;
      text-align: center;
      background-color: rgb(255, 255, 255);
      color: #444;
      border-radius: 6px;
      box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
      padding: 1rem 0;
    }
    button {
      border-radius: 3px;
    }
    .card img {
        width: 3rem;
        margin: 0.8rem auto;
    }
    .card .timer-on {
      margin: 0.2rem auto;
    }
    .card .timer-cont {
      margin: 0.2rem 0;
    }
    .card .timer-cont .timer {
      padding: 8px 12px;
      margin: 0 0.2rem;
    }
    .card .timer-cont .plus,
    .card .timer-cont .minus {
      padding: 3px 8px;
    }
    .card a {
      padding: 0.4rem 5rem;
      background-color: #57B973;
      border-radius: 4px;
      color: #fff;
      margin: 0 auto;
      display: inline-block;
      margin-bottom: 1rem;
      transition: 0.12s all ease-in;
    }
    .card a:hover {
      background-color: #2fa751;
    }
    .notification {
      position: absolute;
      right: 12px;
      top: 6px;
    }
    .flex {
      display: flex;
      justify-content: space-around;
      align-items: center;
    }
    .flex-g {
      flex: 1;
    }
    .hamburger-menu {
        position: absolute;
        top: 5px;
        left: 5px;
        cursor: pointer;
        border-radius: 3px;
        overflow: hidden;
        display: none;

    }
    .close {
        position: absolute;
        top: 5px;
        right: 5px;
        cursor: pointer;
        overflow: hidden;
        display: none;
    }
    @media (max-width:1100px) {
        .aside .profile-links a svg {
            display: none;
        }
        .aside .profile-links a {
            text-align: center;
            justify-content: center;
            padding-left: 0;
        }
    }
    @media (max-width:960px) {
        .aside {
            display: none;
            position: fixed;
        }
        .hamburger-menu {
            display: block;
        }
        .close {
            display: block;
        }
        .show-aside {
            display: block;
            width: 30%;
        }
    } 
    @media (max-width:760px) {
        .aside .profile-links a svg {
            display: block;
        }
        .aside .profile-links a span {
            display: none;
        }
        /* .status-cards {
            justify-content: center;
            flex-wrap: wrap;
        } */
    }
    @media (max-width:600px) {
       main {
           height: 100%;
       }
        .status-cards {
            justify-content: center;
            flex-wrap: wrap;
        }
        .show-aside {
            width: 36%;
        }
    }
</style>
































<!-- 
<script></script>
<main>
  <div class="side-menu">
    <div class="brand-name">
        <h1>Brand</h1>
    </div>
    <ul>
        <li><img src="dashboard (2).png" alt="">&nbsp; <span>Dashboard</span> </li>
        <li><img src="reading-book (1).png" alt="">&nbsp;<span>Students</span> </li>
        <li><img src="teacher2.png" alt="">&nbsp;<span>Teachers</span> </li>
        <li><img src="school.png" alt="">&nbsp;<span>Schools</span> </li>
        <li><img src="payment.png" alt="">&nbsp;<span>Income</span> </li>
        <li><img src="help-web-button.png" alt="">&nbsp; <span>Help</span></li>
        <li><img src="settings.png" alt="">&nbsp;<span>Settings</span> </li>
    </ul>
</div>
<div class="container">
    <div class="header">
        <div class="nav">
            <div class="search">
                <input type="text" placeholder="Search..">
                <button type="submit"><img src="search.png" alt=""></button>
            </div>
            <div class="user">
                <a href="#" class="btn">Add New</a>
                <img src="notifications.png" alt="">
                <div class="img-case">
                    <img src="user.png" alt="">
                </div>
            </div>
        </div>
    </div>
    <div class="content">
        <div class="cards">
            <div class="card">
                <div class="box">
                    <h1>2194</h1>
                    <h3>Students</h3>
                </div>
                <div class="icon-case">
                    <img src="students.png" alt="">
                </div>
            </div>
            <div class="card">
                <div class="box">
                    <h1>53</h1>
                    <h3>Teachers</h3>
                </div>
                <div class="icon-case">
                    <img src="teachers.png" alt="">
                </div>
            </div>
            <div class="card">
                <div class="box">
                    <h1>5</h1>
                    <h3>Schools</h3>
                </div>
                <div class="icon-case">
                    <img src="schools.png" alt="">
                </div>
            </div>
            <div class="card">
                <div class="box">
                    <h1>350000</h1>
                    <h3>Income</h3>
                </div>
                <div class="icon-case">
                    <img src="income.png" alt="">
                </div>
            </div>
        </div>
        <div class="content-2">
            <div class="recent-payments">
                <div class="title">
                    <h2>Recent Payments</h2>
                    <a href="#" class="btn">View All</a>
                </div>
                <table>
                    <tr>
                        <th>Name</th>
                        <th>School</th>
                        <th>Amount</th>
                        <th>Option</th>
                    </tr>
                    <tr>
                        <td>John Doe</td>
                        <td>St. James College</td>
                        <td>$120</td>
                        <td><a href="#" class="btn">View</a></td>
                    </tr>
                    <tr>
                        <td>John Doe</td>
                        <td>St. James College</td>
                        <td>$120</td>
                        <td><a href="#" class="btn">View</a></td>
                    </tr>
                    <tr>
                        <td>John Doe</td>
                        <td>St. James College</td>
                        <td>$120</td>
                        <td><a href="#" class="btn">View</a></td>
                    </tr>
                    <tr>
                        <td>John Doe</td>
                        <td>St. James College</td>
                        <td>$120</td>
                        <td><a href="#" class="btn">View</a></td>
                    </tr>
                    <tr>
                        <td>John Doe</td>
                        <td>St. James College</td>
                        <td>$120</td>
                        <td><a href="#" class="btn">View</a></td>
                    </tr>
                    <tr>
                        <td>John Doe</td>
                        <td>St. James College</td>
                        <td>$120</td>
                        <td><a href="#" class="btn">View</a></td>
                    </tr>
                </table>
            </div>
            <div class="new-students">
                <div class="title">
                    <h2>New Students</h2>
                    <a href="#" class="btn">View All</a>
                </div>
                <table>
                    <tr>
                        <th>Profile</th>
                        <th>Name</th>
                        <th>option</th>
                    </tr>
                    <tr>
                        <td><img src="user.png" alt=""></td>
                        <td>John Steve Doe</td>
                        <td><img src="info.png" alt=""></td>
                    </tr>
                    <tr>
                        <td><img src="user.png" alt=""></td>
                        <td>John Steve Doe</td>
                        <td><img src="info.png" alt=""></td>
                    </tr>
                    <tr>
                        <td><img src="user.png" alt=""></td>
                        <td>John Steve Doe</td>
                        <td><img src="info.png" alt=""></td>
                    </tr>
                    <tr>
                        <td><img src="user.png" alt=""></td>
                        <td>John Steve Doe</td>
                        <td><img src="info.png" alt=""></td>
                    </tr>

                </table>
            </div>
        </div>
    </div>
</div>
</main>
 <style>
   * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

main {
    min-height: 100vh;
}

a {
    text-decoration: none;
}

li {
    list-style: none;
}

h1,
h2 {
    color: #444;
}

h3 {
    color: #999;
}

.btn {
    background: #f05462;
    color: white;
    padding: 5px 10px;
    text-align: center;
}

.btn:hover {
    color: #f05462;
    background: white;
    padding: 3px 8px;
    border: 2px solid #f05462;
}

.title {
    display: flex;
    align-items: center;
    justify-content: space-around;
    padding: 15px 10px;
    border-bottom: 2px solid #999;
}

table {
    padding: 10px;
}

th,
td {
    text-align: left;
    padding: 8px;
}

.side-menu {
    position: fixed;
    background: #f05462;
    width: 20vw;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

.side-menu .brand-name {
    height: 10vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

.side-menu li {
    font-size: 24px;
    padding: 10px 40px;
    color: white;
    display: flex;
    align-items: center;
}

.side-menu li:hover {
    background: white;
    color: #f05462;
}

.container {
    position: absolute;
    right: 0;
    width: 80vw;
    height: 100vh;
    background: #f1f1f1;
}

.container .header {
    position: fixed;
    top: 0;
    right: 0;
    width: 80vw;
    height: 10vh;
    background: white;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    z-index: 1;
}

.container .header .nav {
    width: 90%;
    display: flex;
    align-items: center;
}

.container .header .nav .search {
    flex: 3;
    display: flex;
    justify-content: center;
}

.container .header .nav .search input[type=text] {
    border: none;
    background: #f1f1f1;
    padding: 10px;
    width: 50%;
}

.container .header .nav .search button {
    width: 40px;
    height: 40px;
    border: none;
    display: flex;
    align-items: center;
    justify-content: center;
}

.container .header .nav .search button img {
    width: 30px;
    height: 30px;
}

.container .header .nav .user {
    flex: 1;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.container .header .nav .user img {
    width: 40px;
    height: 40px;
}

.container .header .nav .user .img-case {
    position: relative;
    width: 50px;
    height: 50px;
}

.container .header .nav .user .img-case img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

.container .content {
    position: relative;
    margin-top: 10vh;
    min-height: 90vh;
    background: #f1f1f1;
}

.container .content .cards {
    padding: 20px 15px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
}

.container .content .cards .card {
    width: 250px;
    height: 150px;
    background: white;
    margin: 20px 10px;
    display: flex;
    align-items: center;
    justify-content: space-around;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

.container .content .content-2 {
    min-height: 60vh;
    display: flex;
    justify-content: space-around;
    align-items: flex-start;
    flex-wrap: wrap;
}

.container .content .content-2 .recent-payments {
    min-height: 50vh;
    flex: 5;
    background: white;
    margin: 0 25px 25px 25px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    display: flex;
    flex-direction: column;
}

.container .content .content-2 .new-students {
    flex: 2;
    background: white;
    min-height: 50vh;
    margin: 0 25px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    display: flex;
    flex-direction: column;
}

.container .content .content-2 .new-students table td:nth-child(1) img {
    height: 40px;
    width: 40px;
}

@media screen and (max-width: 1050px) {
    .side-menu li {
        font-size: 18px;
    }
}

@media screen and (max-width: 940px) {
    .side-menu li span {
        display: none;
    }
    .side-menu {
        align-items: center;
    }
    .side-menu li img {
        width: 40px;
        height: 40px;
    }
    .side-menu li:hover {
        background: #f05462;
        padding: 8px 38px;
        border: 2px solid white;
    }
}

@media screen and (max-width:536px) {
    .brand-name h1 {
        font-size: 16px;
    }
    .container .content .cards {
        justify-content: center;
    }
    .side-menu li img {
        width: 30px;
        height: 30px;
    }
    .container .content .content-2 .recent-payments table th:nth-child(2),
    .container .content .content-2 .recent-payments table td:nth-child(2) {
        display: none;
    }
}
 </style> -->