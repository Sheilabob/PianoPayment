<script>
	let amountDue = 75;
	let amountPaid = 75;
	let dateDue = new Date();
	let datePaid = new Date('02/08/2023');

	let paymentRecordArray = [{
		studentName: 'Sheila',
		datePaid: '01/07/23',
		amount: 75,
		method: 'Paypal'
	}, {
		studentName: 'Student',
		datePaid: '01/08/23',
		amount: 85,
		method: 'Check'
	}]
	let sum = 0;



	console.log(paymentRecordArray.filter(record => record.datePaid.slice(0,2) === '01').map(record =>parseInt(record.amount)).reduce(function(a, b){
  return a + b;
}))


	const handlePayment = (e) => {
		amountPaid = e.target.value
	}
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

	function getFormattedDate(date) {
  var year = date.getFullYear();

  var month = (1 + date.getMonth()).toString();
  month = month.length > 1 ? month : '0' + month;

  var day = date.getDate().toString();
  day = day.length > 1 ? day : '0' + day;
  
  return month + '/' + day + '/' + year;
}
const submitPaymentInfo = () => {
	paymentRecordArray.push({studentName: 'New Notsetyet',
		datePaid: getFormattedDate(new Date(datePaid)),
		amount: amountPaid,
		method: 'Notsetyet'})
console.log(paymentRecordArray)
paymentRecordArray = paymentRecordArray

}

$: janPayments = paymentRecordArray.filter(record => record.datePaid.slice(0,2) === '01').map(record =>parseInt(record.amount)).reduce(function(a, b){
  return a + b;
})



</script>

<main>
	<h1 style="{dateDue.getTime() >= new Date(datePaid).getTime() ? 'color:green' : 'color:red'}">Welcome to Piano Pay! {name}</h1>
	<p style="{+amountPaid >= amountDue ? 'color:green' : 'color:red'}">An app to track payments. {beltColor} belt</p>
	<button on:click={handleClick}>update belt color</button>
	<input type="text" bind:value={beltColor}>
	<h2>Student Name: Sheila Strahan</h2>
	<h3>Amount Due: ${amountDue}</h3>
	<h3>Due Date: {getFormattedDate(dateDue)}</h3>
	<div class="payment-form">
	<h3>Input Payment Information:</h3>
	<label for="date-paid">Date:</label>
	<input type="date" id="date-paid" bind:value={datePaid} />
	<label for="amt-paid">Amount Paid:</label>
	$<input type="text" id="amt-paid" bind:value={amountPaid} />
	<label for="pmt-method">Payment Method</label>
	<select id="pmt-method">
		<option value="cash">Cash</option>
		<option value="check">Check</option>
		<option calue="paypal">Paypal</option>
	</select>
	<div>
	<button on:click={submitPaymentInfo}>Submit Payment Info</button>
</div>
</div>
	<h3>Payment History</h3>
<table>
	<thead>
		<tr>
			<th>Name</th>
			<th>Date Paid</th>
			<th>Amount</th>
			<th>Method</th>
		</tr>
	</thead>
		{#each paymentRecordArray as paymentRecord}
		<tbody >
<tr class="payment-record">
		<td>{paymentRecord.studentName}</td>
		<td>{paymentRecord.datePaid}</td>
		<td>${paymentRecord.amount}</td>
		<td>{paymentRecord.method}</td>
	</tr>
	</tbody>

		{/each}
</table>
	<h3>Total for January</h3>
	${janPayments}
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

	tr.payment-record td {
		border-bottom: 2px solid #7db2e0;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>