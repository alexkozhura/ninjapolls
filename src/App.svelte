<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import PollList from './components/PollList.svelte';
	import Tabs from './shared/Tabs.svelte';
	import CreatePollForm from './components/CreatePollForm.svelte';

	// tabs
	let items = ['Current Polls', 'Add New Poll'];
	// also need to say which of them are going to be active
	let activeItem = 'Current Polls';

	const tabChange = (e) => {
		activeItem = e.detail;
	}


  const handleAdd = (e) => {
	activeItem = 'Current Polls';
  }

</script>

<Header />
<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange}/>
	{#if activeItem === 'Current Polls'}
		<PollList />
	{:else if activeItem === 'Add New Poll'}
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