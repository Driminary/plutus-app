<script>
    let people = [
		{ name: 'Tom', favcolour: 'Orange', age: 26, id: 1 },
		{ name: 'Emily', favcolour: 'Pink', age: 24, id: 2 },
		{ name: 'Bob', favcolour: 'Blue', age: 40, id: 3 }
    ];

    const removePerson = (id) => {
        people = people.filter((p) => p.id != id)
    }

</script>

<main>
    {#each people as person (person.id)}
    <div>
        <h4>Name: {person.name}</h4>
        <p style="color: {person.favcolour}">Favourite Colour: {person.favcolour}</p>
        <p>Age: {person.age} 
            {#if person.age > 30}
            👴🏻
            {:else if person.age > 25}
            🧑
            {:else}
            👶
            {/if}
        </p>
        <button on:click={() => removePerson(person.id)}>Delete</button>
    </div>
    {:else}
     <p>No people to show!</p>
    {/each}
</main>