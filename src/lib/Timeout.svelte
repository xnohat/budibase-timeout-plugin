<script>
  import { createEventDispatcher, onDestroy } from "svelte";
  import stopwatchSvg from './icons/stopwatch.svg';

  const dispatch = createEventDispatcher();
  export let timeout;
  export let display = true;
  export let text = "Timeout";

  let timeoutID = null;

  if (timeout > 0) {
    timeoutID = window.setTimeout(() => { dispatch("trigger"); }, timeout * 1000);
  }
  onDestroy(() => {
    if(timeoutID) window.clearTimeout(timeoutID);
  });
</script>

{#if display}
  <div class="container">
    {@html stopwatchSvg} 
    <span>{text}</span>
  </div>
{/if}

<style>
  .container {
    display: flex;
    align-items: center;
    gap: 5px;
  }
</style>
