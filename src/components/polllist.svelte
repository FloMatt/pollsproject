<script>
  import { onMount } from "svelte";
  import PollStore from "../stores/pollstore.js";
  import Polldetails from "./polldetails.svelte";
  import { onDestroy } from "svelte";
  //export let polls = [];
</script>

<div class="poll-list">
  {#each $PollStore as poll (poll.id)}
    <div><Polldetails {poll} /></div>
  {/each}
</div>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }
</style>
