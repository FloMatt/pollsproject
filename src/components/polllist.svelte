<script>
  import PollStore from "../stores/pollstore.js";
  import Polldetails from "./polldetails.svelte";
  export let polls = [];

  PollStore.subscribe((data) => {
    polls = data;
  });
</script>

<div class="poll-list">
  {#each polls as poll (poll.id)}
    <div><Polldetails {poll} on:vote /></div>
  {/each}
</div>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }
</style>
