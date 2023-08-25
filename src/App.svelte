<script>
  import Header from "./components/header.svelte";
  import Footer from "./components/footer.svelte";
  import PollList from "./components/polllist.svelte";
  import Tabs from "./shared/tabs.svelte";
  import CreatePollForm from "./components/createPollForm.svelte";

  //tabs
  let items = ["Current Polls", "Add New Poll"];
  let activeitem = "Current Polls";
  const tabChange = (e) => {
    activeitem = e.detail;
  };

  const handleAdd = (e) => {
    const poll = e.detail;
    polls = [poll, ...polls];

    activeitem = "Current Polls";
  };

  const handleVote = (e) => {
    const { id, option } = e.detail;
    let copiedPolls = [...polls];
    let upvotedPoll = copiedPolls.find((poll) => poll.id == id);

    if (option === "a") {
      upvotedPoll.votesA++;
    }
    if (option === "b") {
      upvotedPoll.votesB++;
    }

    polls = copiedPolls;
  };
</script>

<Header />
<main>
  <Tabs {activeitem} {items} on:tabChange={tabChange} />
  {#if activeitem === "Current Polls"}
    <PollList on:vote={handleVote} />
  {:else if activeitem === "Add New Poll"}
    <CreatePollForm on:add={handleAdd} />
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>
