<script>
    import { Link } from "svelte-routing";
  
    export let to = "";
  
    // @ts-ignore
    function getProps({ href, isPartiallyCurrent, isCurrent }) {
      const isActive = href === "/" ? isCurrent : isPartiallyCurrent || isCurrent;
  
      // The object returned here is spread on the anchor element's attributes
      if (isActive) {
        return { class: "active" };
      }
      return {};
    }
  </script>
  
  <Link to="{to}" getProps="{getProps}">
    <slot />
  </Link>