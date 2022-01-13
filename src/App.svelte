<script>
	import Footer from "./Components/Footer.svelte";
	import Header from "./Components/Header.svelte";
    import Tabs from "./shared/Tabs.svelte";
	import PollForm from './Components/PollForm.svelte'
	import PollList from './Components/PollList.svelte'

	//items array for polls
	let items = ['Current Polls','Add New Poll'];
	//active selected poll
	let activeItem = 'Current Polls'
	
	const tabChange = (e) => {
		activeItem =e.detail
	}

	let polls = [
		{
			id:1,
			question: 'Java or C/C++',
			ans1: 'Java',
			ans2: 'C/C++',
			votes1: 99,
			votes2: 1,
		},
	];

	const handleAdd = (e) => {
		const poll = e.detail
		polls = [poll,...polls]
		console.log(polls);
		activeItem = 'Current Polls'
	}

	const handleVote = (e) => {
		const{id,option} = e.detail
		//copying original polls
		let copiedPoll = [...polls]
		//replacing new with old polls
		let votedPoll = copiedPoll.find((poll)=>poll.id === id)
		//checking for votes
		if(option==='1'){
			votedPoll.votes1++;
		} if(option==='2') {
			votedPoll.votes2++;
		}
		//copying new polls to original polls
		polls = copiedPoll
	}
</script>

<Header/>
	<main>
		<Tabs items={items} activeItem={activeItem} on:tabChange={tabChange}/>
		{#if activeItem === 'Current Polls'}
			<PollList polls={polls} on:vote={handleVote}/>
		{:else if activeItem==='Add New Poll'}
			<PollForm on:add={handleAdd}/> 
		{/if}
	</main>
<Footer/>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>