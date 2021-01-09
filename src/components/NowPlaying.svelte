<script lang='ts'>
  import Axios from 'axios';
  import Movie from './Movie.svelte';
  import type { NowPlaying } from '../types/movie';
  const headerTitle = 'Now Playing';

  const getNowPlaying = async () => {
    try{
      const {data} = await Axios.get<NowPlaying>(
      'https://api.themoviedb.org/3/movie/now_playing?language=ko®ion=KR',
      {
        headers: {
          'Content-Type': 'application/json;charset=utf-8',
          'Authorization': 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI2OTc2ODJlMzIwZmU4ODdjMjljODk3MjIzOGUxODkyNSIsInN1YiI6IjVmM2Y1MmQwMTlhYjU5MDAzNjFkYjUwNiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.BR9IiaCG3OiWTTrcxItmXkps8mP-H-VS6kIixplZeK8'
        }
      }

    )
    console.log(data);
    return data;
    } catch(e){
      throw new Error('error')
    }
  }
</script>

<style>
.container {
  padding: 1rem;
}
.header {
  font-size: 3rem;
}
.movie-list-container {
  margin: 1rem 0;
}

.movie-list {
  display: flex;
}

.movie + .movie {
  margin-left: 1rem;
}



</style>

<div class=container>
  <h1 class=header>{ headerTitle }</h1>
  <section class=movie-list-container>
    {#await getNowPlaying()}
      <p>loading</p>
    {:then movies}
      <ol class=movie-list>
        {#each movies.results as movie}
          <li class=movie>
            <Movie
              movie={movie}
            />
          </li>
        {/each}
      </ol>
    {:catch error}
      <p>{error.message}</p>
    {/await}
  </section>
</div>
