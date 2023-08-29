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

  const handleAdd = () => {
    activeitem = "Current Polls";
  };
</script>

<Header />
<main>
  <Tabs {activeitem} {items} on:tabChange={tabChange} />
  {#if activeitem === "Current Polls"}
    <PollList />
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
