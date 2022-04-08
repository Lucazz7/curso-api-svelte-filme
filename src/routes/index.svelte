<script context="module">
    export async function load({fetch}){
        const res = await fetch(`
https://api.themoviedb.org/3/movie/popular?api_key=a339283f39c01f20663e7e25fa7fd2d7&language=en-US&page=1`);
        const data = await res.json();
        console.log(data);
        if(res.ok){
            return{
                props: {popular: data.results} 
            }
        }
    }
</script>


<script>
// @ts-nocheck

    import FilmesPopular from "../components/FilmesPopular.svelte";
    import SearchMovies from "../components/SearchMovies.svelte";
    export let popular;
    import {fly} from 'svelte/transition';
</script>


<section in:fly={{y: 50, duration: 500}} out:fly={{ duration: 500}}>
    <SearchMovies/>
    <FilmesPopular popular={popular}/>
</section>