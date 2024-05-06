<script>
  import { getContext } from "svelte";
  import Timeout from "./lib/Timeout.svelte";

  export let trigger;
  export let timeout;
  export let display;
  export let text;

  const { styleable } = getContext("sdk");
  const component = getContext("component");
</script>

<div use:styleable={$component.styles}>
  <Timeout on:trigger={trigger} timeout={timeout} display={display} text={text}/>
</div>
