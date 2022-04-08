<script context="module">
    export async function load({fetch, params}){
        const res = await fetch(`https://api.themoviedb.org/3/movie/${params.id}?api_key=a339283f39c01f20663e7e25fa7fd2d7&language=en-US`);
        const filmeDetalhes = await res.json();
        if(res.ok){
            return{
                props: {filmeDetalhes} 
            }
        }
    }
</script>


<script>
    export let filmeDetalhes;
    import {fly} from 'svelte/transition';
</script>


<div class="filmeDetalhes" in:fly={{y: 50, duration: 500}} out:fly={{ duration: 500}}>
    <div class="img-container">
        <img src={'https://image.tmdb.org/t/p/original' + filmeDetalhes.backdrop_path} 
            alt={filmeDetalhes.title}
        />
    </div>
    <div class="txt-container">
        <h1>{filmeDetalhes.title}</h1>
        <p class="overview">{filmeDetalhes.overview}</p>
        <p><span> Release Date </span>
            {filmeDetalhes.release_date} <br/>
            <span> Budget: </span>
            {filmeDetalhes.budget} <br/>
            <span> Rating :</span>
            {filmeDetalhes.vote_average} <br/>
            <span> RunTime </span>
            {filmeDetalhes.runtime} <br/>
        </p>
    </div>
</div>

<style>
    h1  {
        padding: 1rem 0rem 2rem;
        color: white;
    }
    p {
        padding: 1rem 0rem;
        color: white;
    }
    .img-container {
        width: 100%;
    }
    img {
        width: 100%;
        border-radius: 1rem;
    }
    .filmeDetalhes {
        margin: 2rem 20%;
    }
    span {
        font-weight: bold;
        color: white;
    }
</style>