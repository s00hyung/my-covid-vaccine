<script>
    /* IMPORT */
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    /* PROPS */
    export let dose = {};
    export let vaccineTypes = [];

    let verbose = ["First", "Second", "Third", "Fourth"];

    /* FUNCTIONS */
    function removeDose() {
        dispatch("remove", dose);
    }

    function updateDose() {
        dispatch("update", dose);
    }
</script>

<div class="box">
    <div class="content is-normal">
        <h1>{verbose[dose.id]} Dose</h1>
    </div>
    <div class="field is-horizontal">
        <div class="field-label">
            <label class="label" for="vaccine-type">Type</label>
        </div>
        <div class="field-body">
            <div class="control">
                {#if dose.type !== ""}
                    <div class="select" id="vaacine-type">
                        <select bind:value={dose.type} on:change={updateDose}>
                            {#each vaccineTypes as vaccineType}
                                <option>{vaccineType}</option>
                            {/each}
                        </select>
                    </div>
                {:else}
                    <div class="select is-danger" id="vaacine-type">
                        <select bind:value={dose.type} on:change={updateDose}>
                            {#each vaccineTypes as vaccineType}
                                <option>{vaccineType}</option>
                            {/each}
                        </select>
                    </div>
                {/if}
                <p class="help">Choose vaccine type</p>
            </div>
        </div>
    </div>
    <div class="field is-horizontal">
        <div class="field-label">
            <label class="label" for="vaccine-date">Date</label>
        </div>
        <div class="field-body">
            <div class="control">
                <input
                    type="date"
                    id="vaccine-date"
                    bind:value={dose.date}
                    on:change={updateDose}
                />
                <p class="help">Choose vaccinated date</p>
            </div>
        </div>
    </div>
    <button
        class="button is-fullwidth is-danger is-light"
        on:click={removeDose}
    >
        Remove
    </button>
</div>
