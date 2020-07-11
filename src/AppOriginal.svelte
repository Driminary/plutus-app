<script>
	let firstName = 'Tom';
	let lastName = 'Anderson';

    $: fullName = `${firstName} ${lastName}`;
    $: {
        console.log("Something changed! New value for fullName:")
        console.log(fullName); 
    }
</script>

<main>
	<h1>Hello {fullName}!</h1>
    <p>
        <label for="firstName">First name is: </label>
        <input id="firstName" type="text" bind:value={firstName}>
        <br />
        <label for="lastName">Last name is: </label>
        <input id="lastName" type="text" bind:value={lastName}>
    </p>

</main>