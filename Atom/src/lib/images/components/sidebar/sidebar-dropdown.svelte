<script lang="ts">
import "./sidebar-drop.css"
import { Router, Route } from "svelte-routing";
  import NavLink from "../Link.svelte";
  import Home from '../../../../routes/about/+page.svelte'
  import Page from '../../../../routes/sverdle/+page.svelte'
  import NotFound from '../../../../routes/sverdle/how-to-play/+page.svelte'

  // routes
  const routes = {
    '/': Home,
    '/page' : Page,
    '*': NotFound,
  };
  // export let url = "";

// import "./sidebar.js"
// let arrow = document.querySelectorAll(".arrow");
//   for (var i = 0; i < arrow.length; i++) {
//     arrow[i].addEventListener("click", (e)=>{
//    let arrowParent = e.target.parentElement.parentElement;//selecting main parent of arrow
//    arrowParent.classList.toggle("showMenu");
//     });
//   }
//   let sidebar = document.querySelector(".sidebar");
//   let sidebarBtn = document.querySelector(".bx-menu");
//   console.log(sidebarBtn);
//   sidebarBtn.addEventListener("click", ()=>{
//     sidebar.classList.toggle("close");
//   });

let close = false;
let toggleMenu = () => {
    close = !close
    if (close) {
        console.log("Toggle On")
    }
    else {
        console.log("Toggle off")
    }
}
</script>
<!-- <Router url="{url}"> -->
  <div class="sidebar close" class:close>
    <div class="logo-details">
      <i class='bx bxl-c-plus-plus'></i>
      <span class="logo_name">Atom Cloud</span>
    </div>
    <ul class="nav-links">
      <li>
        <!-- <NavLink to="/"> -->
          <a href="/">
            <slot name="icon">
              <i class='bx bx-grid-alt' ></i>
            </slot>
            <span class="link_name">
              <slot name="Name">
                Dashboard
              </slot>
            </span>
          </a>
        <!-- </NavLink> -->
        <ul class="sub-menu blank">
          <!-- <NavLink to="page"> -->
            <li><a class="link_name" href="/page">Category</a></li>
          <!-- </NavLink> -->
        </ul>
      </li>
      <li>
        <div class="iocn-link">
          <a href="/">
            <i class='bx bx-collection' ></i>
            <span class="link_name">Category</span>
          </a>
          <i class='bx bxs-chevron-down arrow' ></i>
        </div>
        <ul class="sub-menu">
          <li><a class="link_name" href="/">Category</a></li>
          <li><a href="/">HTML & CSS</a></li>
          <li><a href="/">JavaScript</a></li>
          <li><a href="/">PHP & MySQL</a></li>
        </ul>
      </li>
      <li>
        <div class="iocn-link">
          <!-- <NavLink to="not found"> -->
            <a href="/">
              <i class='bx bx-book-alt' ></i>
              <span class="link_name">Posts</span>
            </a>
            <i class='bx bxs-chevron-down arrow' ></i>
          <!-- </NavLink> -->
        </div>
        <ul class="sub-menu">
          <li><a class="link_name" href="/">Posts</a></li>
          <li><a href="/">Web Design</a></li>
          <li><a href="/">Login Form</a></li>
          <li><a href="/">Card Design</a></li>
        </ul>
      </li>
      <li>
        <a href="/">
          <i class='bx bx-pie-chart-alt-2' ></i>
          <span class="link_name">Analytics</span>
        </a>
        <ul class="sub-menu blank">
          <li><a class="link_name" href="/">Analytics</a></li>
        </ul>
      </li>
      <li>
        <a href="/">
          <i class='bx bx-line-chart' ></i>
          <span class="link_name">Chart</span>
        </a>
        <ul class="sub-menu blank">
          <li><a class="link_name" href="/">Chart</a></li>
        </ul>
      </li>
      <li>
        <div class="iocn-link">
          <a href="/">
            <i class='bx bx-plug' ></i>
            <span class="link_name">Plugins</span>
          </a>
          <i class='bx bxs-chevron-down arrow' ></i>
        </div>
        <ul class="sub-menu">
          <li><a class="link_name" href="/">Plugins</a></li>
          <li><a href="/">UI Face</a></li>
          <li><a href="/">Pigments</a></li>
          <li><a href="/">Box Icons</a></li>
        </ul>
      </li>
      <li>
        <a href="/">
          <i class='bx bx-compass' ></i>
          <span class="link_name">Explore</span>
        </a>
        <ul class="sub-menu blank">
          <li><a class="link_name" href="/">Explore</a></li>
        </ul>
      </li>
      <li>
        <a href="/">
          <i class='bx bx-history'></i>
          <span class="link_name">History</span>
        </a>
        <ul class="sub-menu blank">
          <li><a class="link_name" href="/">History</a></li>
        </ul>
      </li>
      <li>
        <a href="/">
          <i class='bx bx-cog' ></i>
          <span class="link_name">Setting</span>
        </a>
        <ul class="sub-menu blank">
          <li><a class="link_name" href="/">Setting</a></li>
        </ul>
      </li>
      <li>
    <div class="profile-details">
      <div class="profile-content">
        <img src="https://cdn.pixabay.com/photo/2021/03/03/10/20/portrait-6064965_960_720.jpg" alt="profileImg">
      </div>
      <div class="name-job">
        <div class="profile_name">Abdul Mujeeb</div>
        <div class="job">Web Desginer</div>
      </div>
      <i class='bx bx-log-out' ></i>
    </div>
  </li>
</ul>
  </div>
  <section class="home-section">
      <button on:click={toggleMenu}>
        {#if close}
        <i class="fa fa-fw fa-angle-left icon"></i>
        {:else}
        <i class="fa fa-fw fa-angle-right icon"></i>
        {/if}
    </button>
    <div class="home-content">
      <i class='bx bx-menu' class:change={close} on:click={toggleMenu} ></i>
      <slot name="content">
        <span class="text">
          <!-- <Route path="/" component="{Home}" />
          <Route path="page/*" component="{Page}" />
          <Route path="not found" component="{NotFound}" /> -->
            </span>
      </slot>
    </div>
  </section>
<!-- </Router> -->
