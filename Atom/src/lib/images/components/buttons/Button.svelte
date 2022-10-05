<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	export let fab = false;
	export let label = '';
	export let icon = '';
	export let disabled = false;
</script>
<div>
	<button
	{disabled}
	class={fab ? 'fab' : 'btn'}
	on:click={(e) => {
		dispatch('click', e);
	}}
>
<slot />
{#if icon != ''}
<i class="fa {icon}" aria-hidden="true" />
{/if}
{#if label != ''}
{label}
{/if}
</button>
</div>

<style>
	div{
		width: 100%;
	}
	.btn {
		background-position: center;
		transition: background 0.8s;
		width: fit-content;
	}

	.btn:hover {
		background: #47a7f5 radial-gradient(circle, transparent 1%, #47a7f5 1%) center/15000%;
	}

	.btn:active {
		background-color: #6eb9f7;
		background-size: 100%;
		transition: background 0s;
	}

	.fab {
		background-position: center;
		transition: background 0.8s;
		width: 60px;
		height: 60px;
		border-radius: 50%;
	}

	.fab:hover {
		background: #47a7f5 radial-gradient(circle, transparent 1%, #47a7f5 1%) center/15000%;
	}

	.fab:active {
		background-color: #6eb9f7;
		background-size: 100%;
		transition: background 0s;
	}

	button {
		border: none;
		padding: .5em 1.5em;
		font-size: 16px;
		text-transform: uppercase;
		cursor: pointer;
		color: white;
		background-color: #2196f3;
		box-shadow: 0 0 15px 4px rgba(0, 0, 0, 0.06);
		border-radius: 5px;
		outline: none;
		display: inline-block;
	}
  
</style>