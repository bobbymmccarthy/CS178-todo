<script>
	let yes = [0]
	let val = ''
	let toDoList = ['Open you ED account', 'Finish you homework on Time']
	function handleClick(event) {
		// reactive
		toDoList = [...toDoList, val]	
	}
	function handleRemove(todo,i){
		//reactive
		toDoList = toDoList.filter((x) => {
			return x != todo
		})
		yes = yes.filter((x) => {
			return x != i
		})

	}
</script>

<main>
	<h1>Bobby's To Do List</h1>
	<!-- reactive -->
	<input type = text bind:value= {val}>
	<button on:click = {handleClick}> Add</button>
	<ul>
		<!-- control flow -->
		{#each toDoList as todo, i}
			<li>
				<input type = checkbox bind:group ={yes} value = {i}>
				{#if !yes.includes(i)}
					{todo}
				{:else}
					<strike> {todo} </strike>
				{/if}
				<!-- event handling -->
				<button on:click = { () => {return handleRemove(todo, i)}}> Remove</button>
			</li>
		{/each}
	</ul>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
	li {
		list-style-type: none;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>