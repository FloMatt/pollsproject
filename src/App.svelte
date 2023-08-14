<script>
  import Header from "./components/header.svelte";
  import Footer from "./components/footer.svelte";
  import Tabs from "./shared/tabs.svelte";
  import CreatePollForm from "./components/createPollForm.svelte";

  //tabs
  let items = ["Current Polls", "Add New Poll"];
  let activeitem = "Current Polls";
  const tabChange = (e) => {
    activeitem = e.detail;
  };
</script>

<Header />
<main>
  <Tabs {activeitem} {items} on:tabChange={tabChange} />
  {#if activeitem === "Current Polls"}
    <p>Poll list componnet goes here</p>
  {:else if activeitem === "Add New Poll"}
    <CreatePollForm />
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>
