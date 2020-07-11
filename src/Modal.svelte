<script>
    export let showModal = false;
    export let isAlert = false;
</script>

{#if showModal}
    <div class="backdrop" class:alert={isAlert} on:click|self >
        <div class="modal">
            <slot></slot>
        </div>
    </div>
{/if}

<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0,0,0,0.8);
    }

    .modal {
        padding: 1rem;
        border-radius: 1rem;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }

    .alert .modal {
        background: crimson;
        color: white;
    }
</style>