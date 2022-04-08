<script context="module">
    export async function load({fetch, params}){
        const res = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=a339283f39c01f20663e7e25fa7fd2d7&language=en-US&query=${params.id}&page=1&include_adult=false`);

        const data = await res.json();
        console.log(data);
        if(res.ok){
            return{
                props: {searchedMovie: data.results} 
            }
        }
    }
</script>

<script>
    import CardFilme from "../../components/CardFilme.svelte";
    export let searchedMovie;
</script>

<div class="searched-movies">
    {#each searchedMovie as filmes}
        <CardFilme {filmes}/>
    {/each}
</div>

<style>
    .searched-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-column-gap: 1rem;
        grid-row-gap: 2rem;
        height: 20vh;
    }
</style>