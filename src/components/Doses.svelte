<script>
    /* IMPORT */
    import Dose from "./Dose.svelte";

    /* PROPS */
    export let doses = [];
    export let vaccineTypes = [];

    /* REACT */
    $: numOfDose = doses.length;
    $: newDoseId = numOfDose ? Math.max(...doses.map((d) => d.id)) + 1 : 0;

    /* FUNCTIONS */
    const todayDate = new Date().toISOString().substring(0, 10);
    function removeDose(dose) {
        doses = doses.filter((d) => d.id !== dose.id);
    }

    function addDose() {
        doses = [...doses, { id: newDoseId, type: "", date: todayDate }];
    }

    function updateDose(dose) {
        const i = doses.findIndex((d) => d.id === dose.id);
        doses[i] = dose;
    }
</script>

<div class="container">
    {#each doses as dose, i}
        <Dose
            {dose}
            {vaccineTypes}
            on:remove={(e) => removeDose(e.detail)}
            on:update={(e) => updateDose(e.detail)}
        />
    {:else}
        Add new dose
    {/each}

    <div class="buttons">
        {#if numOfDose < 4}
            <button
                class="button is-link is-light is-fullwidth"
                on:click|preventDefault={addDose}
            >
                Add Dose
            </button>
        {:else}
            <button class="button is-link is-light is-fullwidth" disabled>
                You can not add more dose
            </button>
        {/if}
    </div>
</div>
