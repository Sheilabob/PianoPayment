<script>
	let amountDue = 75;
	let amountPaid = '75';
	let paymentColor = 'black';

	const handlePayment = (e) => {
		amountPaid = e.target.value
	}
console.log(amountPaid)
	if (amountPaid == '85') {
		paymentColor = 'green'
	}
	if (amountPaid == '65') {
		paymentColor = 'red'
	}

	let name = 'Yoshi'
	let beltColor = 'black';

	const handleClick = () => {
		beltColor = 'orange';
	}
	const handleInput = (e) => {
		beltColor = e.target.value
	}
</script>

<main>
	<h1>Welcome to Piano Pay! {name}</h1>
	<p style="{+amountPaid >= 75 ? 'color:green' : 'color:red'}">An app to track. {beltColor} belt</p>
	<button on:click={handleClick}>update belt color</button>
	<input type="text" bind:value={beltColor}>

	<label for="amt-paid">Amount Paid:</label>
	<input type="text" id="amt-paid" bind:value={amountPaid}>
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

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>