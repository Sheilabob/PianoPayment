<script>
	let amountDue = 75;
	let amountPaid = 75;
	let dateDue = new Date('02/08/2023');
	let datePaid = new Date('02/08/2023');
	let paymentColor = 'black';
	let dateColor = 'black';

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

	if (datePaid == '02/08/2023') {
		dateColor = 'green'
	}
	if (datePaid == '02/09/2023') {
		dateColor = 'red'
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
	<h1 style="{dateDue.getTime() >= new Date(datePaid).getTime() ? 'color:green' : 'color:red'}">Welcome to Piano Pay! {name}</h1>
	<p style="{+amountPaid >= amountDue ? 'color:green' : 'color:red'}">An app to track payments. {beltColor} belt</p>
	<button on:click={handleClick}>update belt color</button>
	<input type="text" bind:value={beltColor}>

	<label for="date-paid">Date:</label>
	<input type="date" id="date-paid" bind:value={datePaid} />
	<label for="amt-paid">Amount Paid:</label>
	<input type="text" id="amt-paid" bind:value={amountPaid} />
	<label for="pmt-method">Payment Method</label>
	<select id="pmt-method">
		<option value="cash">Cash</option>
		<option value="check">Check</option>
		<option calue="paypal">Paypal</option>
	</select>
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