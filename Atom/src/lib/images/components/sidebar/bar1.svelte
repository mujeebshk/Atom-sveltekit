<script>
  	import { page } from '$app/stores';

    let navActive = false;
    const toggleNav = () => {
      navActive = !navActive;
    };
  </script>
  
  <style>
    /* main {
      font-family: sans-serif;
    } */
  
    .menu {
      position: fixed;
      background: black;
      left: 0;
      top: 4em;
      bottom: 0;
      overflow: hidden;
      width: 80px;
      transition: 300ms;
    }
  
    .menu.active {
      width: 400px;
    }
  
    .menu__Item .menu__Link {
      color: white;
    }
  
    .menu__List {
      all: unset;
      display: block;
      width: 100%;
    }
  
    .menu__Item {
      display: block;
    }
  
    .menu__Link {
      display: block;
      padding: 5px;
      margin: 15px;
      text-decoration: none;
      white-space: nowrap;
      border-radius: 30px;
      color: transparent;
      transition: 300ms;
    }
  
    .menu__Link:hover {
      color: orange;
      background: #555;
    }
  
    .menu__Link::before {
      content: attr(title);
      display: inline-block;
      width: 40px;
      height: 40px;
      line-height: 40px;
      text-align: center;
      margin-right: 20px;
      color: orange;
    }
  
    .menu__Toggle {
      all: unset;
      font-size: 14px;
      color: red;
      padding: 15px;
      font-weight: bold;
      background: #333;
      margin: 20px;
      cursor: pointer;
    }
  
    .wrapper {
      margin-left: 80px;
      padding-left: 40px;
      transition: 300ms;
    }
  
    .wrapper.active {
      margin-left: 400px;
    }
  </style>
  

    <nav class="menu" class:active="{ navActive }">
      <button class="menu__Toggle" on:click="{ () => toggleNav() }">{ navActive ? '<' : '>'}</button>
      <ul class="menu__List">
        <li class="menu__Item"><a title="🐤" class="menu__Link" href="a#">
          <i class="fa fa-fw fa-home"></i>
          Link 1</a></li>
        <li class="menu__Item"><a title="🐶" class="menu__Link" href="b#">Link with more text</a></li>
        <li class="menu__Item"><a title="🙈" class="menu__Link" href="c#">Link 3</a></li>
        <li class:active={$page.url.pathname === '/about'}>
          <a href="/about" class="menu__Link">About</a>
        </li>
        <li class="menu__Item"><a title="🐻" class="menu__Link" href="d#">Link 4</a></li>
      </ul>
    </nav>
      <div class="wrapper" class:active="{ navActive }">
      <h2>Start editing to see some magic happen!</h2>
      <slot />
    </div>