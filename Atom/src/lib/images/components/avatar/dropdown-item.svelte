<svelte:options tag="my-dropdown-item" />

<script>
  import { getContext , createEventDispatcher } from 'svelte';
	
	const dispatch = createEventDispatcher();
	
  /**
	 * @type {any}
	 */
   export let value;

  function selectValue() {
		dispatch("clicked", value);
    const { select } =  getContext('dropdown');
    select(value)
  }

</script>

<div class="option" on:click={selectValue}>
  <slot></slot>
</div>

<style>
  .option {
    width: 100%;
    padding: 0.5rem;
    cursor: pointer;
    white-space: nowrap;
    z-index: 999;
  }

  .option:hover {
    background: #eee;
    text-decoration: dashed;
  }
</style>