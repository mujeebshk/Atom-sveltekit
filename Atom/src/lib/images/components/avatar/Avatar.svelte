<script>
	import Dropdown from "./dropdown.svelte";
	import DropdownItem from "./dropdown-item.svelte";

</script>


<Dropdown let:updateMe >
  <DropdownItem value="1" on:clicked={updateMe}>Item 1 </DropdownItem>
  <DropdownItem value="2" on:clicked={updateMe}>Item 2</DropdownItem>
  <DropdownItem value="3" on:clicked={updateMe}>Item 3</DropdownItem>
  <DropdownItem value="4" on:clicked={updateMe}>Item 4</DropdownItem>
</Dropdown> 

