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

	// polls
	let polls = [
    {
      id: 1,
      question: 'Python or JavaScript?',
      answerA: 'Python',
      answerB: 'JavaScript',
      votesA: 9,
      votesB: 15,
    },
  ];

  const handleAdd = (e) => {
	const poll = e.detail;
	polls = [poll, ...polls];
	console.log(polls);
	// to return the focus to the list of polls after we've added the new poll
	activeItem = 'Current Polls';
  }

  const handleVote = (e) => {
	const { option, id } = e.detail;
	
	// we create a copy of the polls array here so that we don't cause refresh right away
	let copiedPolls = [...polls];
	let upvotedPoll = copiedPolls.find((poll) => poll.id == id);

	if (option === 'a') {
		upvotedPoll.votesA++;
	}
	if (option === 'b') {
		upvotedPoll.votesB++;
	}

	polls = copiedPolls;
  }
</script>

<Header />
<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange}/>
	{#if activeItem === 'Current Polls'}
		<PollList {polls} on:vote={handleVote}/>
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