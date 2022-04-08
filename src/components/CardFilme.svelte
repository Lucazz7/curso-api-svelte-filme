<script>
    export let filmes;
</script>

<div class="card-filme">
    <a sveltekit:prefetch sveltekit:noscroll href={'/movies/' + filmes.id}>
        <img src={'https://image.tmdb.org/t/p/w500' + filmes.poster_path} alt={filmes.title} />
    </a>
    <div class="description">
        <h2>{filmes.title}</h2>
        <p>{filmes.release_date}</p>
    </div>
</div>



<style>
    img{
        width: 100%;
        height: 40vh;
        object-fit: cover;
        border-radius: 1rem;
        margin-bottom: 1rem;
    }
    h2 {
        font-size: 0.9rem;
        color: white;
    }
    .description {
        height: 5vh;
        color: white;
    }

    p{
        font-size: 0.7rem;
        color: white;
    }

    .card-filme{
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        padding: 1rem;
    }

</style>