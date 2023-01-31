<script>
    export let style = "solid";

</script>

<section class=" {style}">
{#if style === "symbol"}
<p>§</p>
{/if}
</section>

<style>


    p {
        margin: 0;
        padding: 2rem;
        font-size: 1.5rem;
        text-align: center;

        color: var(--color-gray-300);
    }


</style>