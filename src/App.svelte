<script>
	//Introduction
	let name = "Anders";
	import Message from "./components/Message/Message.svelte";

	//Reactivity & Events
	let startExclamation = "Do it";
	let exclamation = startExclamation;
	let clicks = 0, maxClicks = 10;
	$: clicksLeft = maxClicks - clicks;
	$: if(clicks >= maxClicks) {
		exclamation = `Yay! You clicked ${maxClicks} times!`;
		clicks = maxClicks;
		alert(
			`You clicked the red button ${maxClicks} times.\nYou have no clicks left!`
		);
	}
	function buttonHover(){
		if(clicks === 0)
			exclamation = "DO IT! DO IT NOW!"
	}
	function buttonClick(){
		clicks++;
		exclamation = "Good! Do it again!";
	}

	//Props
	import Person from "./components/Student/Student.svelte";
	let students = [
		{name: "Thor", age: 23, favoriteColor: "yellow"},
		{name: "Mette", favoriteColor: "green"},
		{name: "Alex", age: 27, favoriteColor: "blue"}
	];

</script>

<main>

	<!--Introduction-->
	<div>
		<h1>Hello {name}!</h1>
		<Message/>
		<br>
		(Introduction)
	</div>

	<!--Reactivity, If-Else Block & DOM Event-->
	<div>
		<h1>Click The Button!</h1>
		<h2>{exclamation}</h2>
		<p>
			{#if clicks}
				You've clicked the red button {clicks} {clicks === 1 ? 'time' : 'times'}.
			{:else}
				You haven't clicked the red button yet!
			{/if}
			<br>
			You have {clicksLeft ? clicksLeft : "no"} {clicksLeft === 1 ? 'click' : 'clicks'} left.
			<br>
			<button class="red-button" on:click={buttonClick} on:mousemove={buttonHover}>
				CLICK ME!
			</button>
		</p>
		<button on:click={() => {clicks = 0; exclamation = startExclamation;}}>Reset</button>
		<br>
		(Reactivity, If-Else Block & DOM Event)
	</div>

	<!--Props & Each Block-->
	<div>
		<h1>Students</h1>
		{#each students as student, i}
			<h3>Student {i + 1}</h3>
			<Person {...student}/>
		{/each}
		<br>
		(Props & Each Block)
	</div>

</main>

<style>
	main{
		text-align: center;
		width: fit-content;
		position: relative;
		left: 50%;
		transform: translate(-50%, 0);
	}
	div{
		vertical-align: top;
		border: 1px solid black;
		padding: 20px;
		margin: 5px;
		display: inline-block;
	}
	h1{
		margin: 5px;
	}
	h2{
		margin: 0;
	}
	.red-button{
		margin-top: 10px;
		background-color: red;
		font-weight: bold;
	    color: white;
		width: 120px;
		height: 120px;
		border-radius: 50%;
		border: 2px solid black;
	}
	.red-button:active{
		background-color: brown;
	}
	h3{
		margin: 0;
		margin-top: 10px;
	}
</style>