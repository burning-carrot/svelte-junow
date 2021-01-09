<script lang='ts'>
  import type {Movie} from '../types/movie'
  export let movie: Movie

  const {
    title,
    poster_path,
    release_date,
  } = movie;
</script>

<style>
  .container {
    width: 20rem;

    border-top: 1px solid rgba(255,255,255,0.5);
    border-left: 1px solid rgba(255,255,255,0.5);
    border-radius: 8px;
    box-shadow: 20px 20px 50px rgba(0,0,0,0.5);
    backdrop-filter: blur(10px);
  }
  .poster {
    width: 100%;
    border-radius: 8px;
  }

  .info {
    padding: 1rem;
  }
  .title {
    font-size: 1.5rem;
  }

  .release_date {
    color: #FFFFFF;
  }
</style>

<div class='container'>
  <img
    class=poster
    src={`https://image.tmdb.org/t/p/w500${poster_path}`}
    alt={`${title} poster`}
  />
  <div class=info>
    <h1 class=title>{title}</h1>
    <p class=release_date>{release_date}</p>
  </div>
</div>