<script>
    export let text = [];
    if (!text) throw new Error('"text" prop must be defined as a string');
    console.log(text);
</script>

<!-- Pretty numbered list of all notes -->

<section id="endnotes" class="body-text my-16">

    <h4>Endnotes</h4>
    <hr />
    <ol>
        {#each text as note}
            <li class="list-decimal py-4">
                <p>{note.value}</p>
            </li>
        {/each}
    </ol>
</section>

<style>
/* Simple ordered list. */

h4 {
    margin-top: 1rem;
    font-weight: bold;
    font-size: 1.5rem;
}

hr {
    margin-top: 0.5rem;
    margin-bottom: 0.5rem;
    border: 0;
    border-top: 1px solid rgb(64, 64, 64);
    
}

/* Make list numbers bold and accent collored */

li {
    font-weight: bold;
    color: var(--color-primary);
}

p {
    font-weight: normal;
    color: var(--color-text);
}

/* Make the list items look like a list. */


</style>