<svelte:options tag="my-dropdown" />

<script>
  import { setContext } from 'svelte'
  export const url = '/';

  let value = 'Avatar';
  let isMenuVisible = false;
	
	let updateMe = (/** @type {{ detail: any; }} */ e)=> {
		alert(e.detail);
	}
	

  setContext('dropdown', {
    select: (/** @type {string} */ newValue) => {
      value = newValue;
    }
  })

  function toggleMenu() {
    isMenuVisible = !isMenuVisible;
  }

</script>

<div class="dropdown" on:click={toggleMenu}>
  <div class="title">
<img src="https://cdn.pixabay.com/photo/2021/03/03/10/20/portrait-6064965_960_720.jpg" alt="Avatar">
  </div>
  {#if (isMenuVisible)}
  <ul class="options">
    <a href={url}>
        <slot updateMe={updateMe}></slot>
    </a>
  </ul>
  {/if}
</div>

<style>
  img{
    width:2em;
    height: 2em;
    border-radius: 50%;
  }
  .dropdown {
    /* border: 1px solid #ccc; */
    border-radius: 6px;
    position: relative;
  }

  /* .title {
    padding: 0.5rem;
  } */

  .title::after {
    margin-left: 0.5rem;
    /* content: "⏷"; */
  }

  .options {
    position: absolute;
    padding: 0;
    /* top: 0rem; */
    left: 0;
    right: 0;
    width: 5em
  }
</style>