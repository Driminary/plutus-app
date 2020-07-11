<script>

    import { createEventDispatcher } from 'svelte';

    let dispatch = createEventDispatcher();

    let name;
    let favcolour;
    let age;
    let salaryrange;

    let skills = [];

    const handleSubmit = () => {
        console.log(name, favcolour, age, skills, salaryrange)
        const person = {
            name,
            favcolour,
            age,
            salaryrange,
            skills,
            id: Math.floor(Math.random() * (1000)) + 1,
        };
        dispatch('addPerson', person);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name}>
    <input type="text" placeholder="favourite colour" bind:value={favcolour}>
    <input type="number" placeholder="age" bind:value={age}>
    <label>Skills:</label>
    <input type="checkbox" bind:group={skills} value="baking"> Baking<br>
    <input type="checkbox" bind:group={skills} value="driving"> Driving<br>
    <input type="checkbox" bind:group={skills} value="painting"> Painting<br>
    <input type="checkbox" bind:group={skills} value="tidying"> Tidying<br>
    <label>Salary:</label>
    <select bind:value={salaryrange}>
        <option value="0">£0 - £20,000</option>
        <option value="1">£20,001 - £30,000</option>
        <option value="2">£30,001 - £40,000</option>
        <option value="3">£40,001 - £50,000</option>
        <option value="4">£50,001 +</option>
    </select><br>
    <button>Add Person</button>
</form>

<style>
    input[type=number]{
        max-width: 4rem;
    }
    
    input[type=text]{
        max-width: 9rem;
    }
</style>