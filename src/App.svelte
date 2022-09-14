<script>
	import Header from "./components/Header.svelte";
	import Footer from "./components/Footer.svelte";
  	import Tabs from "./shared/tabs.svelte";
  	import CreatePollForm from "./components/CreatePollForm.svelte";
  	import PollList from "./components/PollList.svelte";

	// tabs
	let items = ['Current Polls', 'Add New Poll'];
	let activeItem = items[0];

	let tabChange = (e) => {
		activeItem = e.detail;
	}

	localStorage.setItem("test", "test")

	// Polls
	let polls = [
		{
			id: 1,
			question: "Python or JavaScript?",
			answerA: "Python",
			answerB: "JavaScript",
			votesA: 9,
			votesB: 15
		}
	]

	let onAdd = (e) => {
		activeItem = items[0];
	}

</script>

<Header />
<main>
	<Tabs {items} {activeItem} on:tabChange={tabChange} />
	{#if activeItem === items[0]}
		<PollList {polls} />
	{:else if activeItem === items[1]}
		<CreatePollForm on:add={onAdd} />
	{/if}
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>