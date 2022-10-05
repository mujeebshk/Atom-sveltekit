<script lang="ts">
	import { fade } from 'svelte/transition';
	import Button from "../buttons/Button.svelte"
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();
	const fadeIn = {
		delay: 100,
		duration: 200
	}
	
	const fadeOut = {
		delay: 0,
		duration: 100
	}
	
	let isExpanded = false;

</script>
<div class="sidebar">
	<div class="sidebar-content" style="display: -webkit-box">
		<nav class:expanded={isExpanded}>
			<ul class="lists">
				<li class="list">  <a href="/" class="nav-link"> <i class="fa fa-fw fa-home icon"></i> {#if isExpanded}<span class="link" in:fade="{fadeIn}" out:fade="{fadeOut}">Inbox</span> {/if}</li>
					<li class="list">  <a href="/" class="nav-link"><i class="fa fa-fw fa-wrench icon"></i> {#if isExpanded}<span class="link" in:fade="{fadeIn}" out:fade="{fadeOut}">Starred</span> {/if}</li>
						<li class="list">  <a href="/" class="nav-link"><i class="fa fa-fw fa-user icon"></i> {#if isExpanded}<span class="link" in:fade="{fadeIn}" out:fade="{fadeOut}">Trashed</span> {/if}</li>
						</ul>
						{#if isExpanded}
						<section in:fade="{fadeIn}" out:fade="{fadeOut}" >
							<hr />
							<ul class="lists">
				<h3>
					Folders
				</h3>
				<a href="/" class="nav-link"><li class="list">🧾 Receipts</li></a>
				<a href="/" class="nav-link"><li class="list">🤖 Autofilter</li></a>
			</ul>
		</section>
		{/if}
	</nav>
	<button on:click={() => isExpanded = !isExpanded}>
		{#if isExpanded}
		<i class="fa fa-fw fa-angle-left icon"></i>
		{:else}
		<i class="fa fa-fw fa-angle-right icon"></i>
		{/if}
	</button>
</div>
</div>
<section class="overlay"></section>

<style>
	nav {
		grid-area: nav;
		/* height: 100vw; */
		background-color: #f4f4f4;
		color: #333435;
		transition: ease-out 200ms;
		width: 4em;
		overflow: hidden;
		box-shadow: 0 0 1px rgba(0, 0, 0, 0.1);
		display:grid;

	}

	.expanded {
		transition: ease-out 200ms;
		width: 200px;
	}
	
	ul {
		list-style: none;
		padding: 20px;
		margin: 0;
	}
	
	li {
		width: 10em;
	}
	
	h3 {
		text-transform: uppercase;
		margin: 0;
		padding: 10px 0;
	}
	
	hr {
	  color: white;
		width: 80%;
	}
	
	button {
		border: none;
		background: none;
		color: #A2B7C4;
		text-transform: uppercase;
	}
/* 
 .sidebar {
  position: fixed;
  top: 0;
  left: -100%;
  height: 100%;
  width: 260px;
  padding: 20px 0;
  background-color: #fff;
  box-shadow: 0 5px 1px rgba(0, 0, 0, 0.1);
  transition: all 0.4s ease;
} */

.logo .menu-icon {
  color: #333;
  font-size: 24px;
  margin-right: 14px;
  cursor: pointer;
}
.logo .logo-name {
  color: #333;
  font-size: 22px;
  font-weight: 500;
}

nav.open .sidebar {
  left: 0;
}
nav.open ~ .overlay {
  opacity: 1;
  left: 260px;
  pointer-events: auto;
}

.sidebar .sidebar-content {
  display: flex;
  height: 100%;
  flex-direction: column;
  justify-content: space-between;
  padding: 30px 16px;
}

.sidebar-content .list {
  list-style: none;
}

.list .nav-link {
  display: flex;
  align-items: center;
  margin: 8px 0;
  padding: 14px 12px;
  border-radius: 8px;
  text-decoration: none;
}

.lists .nav-link {
  transition: background-color 0.25s ease;
}
.lists .nav-link:hover {
  background-color: #c7c9cd;
}
.lists .nav-link:hover .icon {
  color: #fff;
}
.lists .nav-link:hover .link {
  color: #fff;
}

.nav-link .icon {
  margin-right: 14px;
  font-size: 20px;
  color: #707070;
}
.nav-link .link {
  font-size: 16px;
  color: #707070;
  font-weight: 400;
}

.overlay {
  position: fixed;
  top: 0;
  left: -100%;
  height: 1000vh;
  width: 200%;
  opacity: 0;
  pointer-events: none;
  transition: all 0.4s ease;
  background: rgba(0, 0, 0, 0.3);
}
</style>