<script>
    export let popular;
    import CardFilme from "./CardFilme.svelte";
</script>


<h3>Filmes Populares</h3>
<div class="filmes-populares">
   {#each popular as filmes }
      <CardFilme {filmes} />
   {/each}
</div>

<style>
    h3 {
        display: flex;
        min-height: 10vh;
        align-items: center;
        justify-content: center;
        color: white;
    }

    .filmes-populares {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-column-gap: 1rem;
        grid-row-gap: 2rem;
        min-height: 10vh;
        align-items: center;
        justify-content: center;
    }
</style>