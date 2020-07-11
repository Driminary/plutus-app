<script>

    import Modal from './Modal.svelte';
    import AddPersonForm from './AddPersonForm.svelte'

    let showModal = false;
    
    let people = [
		{ name: 'Tom', favcolour: 'Orange', age: 26, id: 1 },
		{ name: 'Emily', favcolour: 'Purple', age: 24, id: 2 },
		{ name: 'Bob', favcolour: 'Blue', age: 40, id: 3 }
    ];

    const removePerson = (id) => {
        people = people.filter((p) => p.id != id)
    };

    const toggleModal = () => {
        showModal = !showModal;
    };

    const addPerson = (e) => {
        const person = e.detail;
        people = [person, ...people]
        showModal = false;
    };

</script>

<Modal isAlert={false} {showModal} on:click={toggleModal}>
 <AddPersonForm on:addPerson={addPerson}/>
</Modal>

<main>
    <button on:click|once={toggleModal}>Open Modal</button>
    {#each people as person (person.id)}
    <div>
        <h4>Name: {person.name}</h4>
        <p style="color: {person.favcolour}">Favourite Colour: {person.favcolour}</p>
        <p>Age: <input type="number" bind:value={person.age}> 
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

<style>
    main {
        text-align: center;
        padding: 1rem;
        max-width: 240px;
        margin: 0 auto;
    }

    @media (min-width: 640px) {
        main{
            max-width: none;
        }
    }
    
    input[type=number]{
        max-width: 3rem;
    }
</style>