<template>
    <div class="MovieComponentContainer">
        <h1 class="MovieName">{{ movieData.title }}</h1>
        <img :src="'https://image.tmdb.org/t/p/w500' + movieData.poster_path" :alt="movieData.title + ' poster'"
            class="MoviePoster">
        <div class="MovieTextContainer">
            <div>
                <h2>Release Date:</h2>
                <p>{{ movieData.release_date }}</p>
            </div>
            <div class="Runtime">
                <h2>Runtime:</h2>
                <p>{{ movieData.runtime }} minutes</p>
            </div>
            <!--
            <div>
                <h2>Genres:</h2>
                <p>{{ getGenres(movieData.genres) }}</p>
            </div>
            -->
            <div>
                <h2>Overview:</h2>
                <p>{{ movieData.overview }}</p>
            </div>
            <!--
            <div>
                <h2 class="MovieProducers">Production Companies:</h2>
                <ul class="MovieList">
                    <li v-for="company in movieData.production_companies" :key="company.id">{{ company.name }}</li>
                </ul>
            </div>
            -->
        </div>
    </div>
</template>

<script>
export default {
  name: 'MovieData',
  props: {
    movieData: {
      type: Object,
      required: true
    }
  },
  methods: {
    // getGenres (genres) {
    //   return genres.map(genre => genre.name).join(', ')
    // }
  }
}
</script>

<style>
.MovieList {
    text-align: left;
    list-style-type: square;
}
h2{
    font-size: 16px;
}
h2,
p {
    vertical-align: middle;
    line-height: 24px;
    height: fit-content;
    margin-left: 15%;
    display: flex;
    margin-left: 265px;
    width:480px;
}

.MoviePoster {
    max-width: 250px;
    position: absolute;
    margin-top:0px ;
}

.MovieComponentContainer {
    border: 4px solid beige;
    border-radius: round 2px;
    border-left: none;
    border-right: none;
    border-top: none;
}

.MovieTextContainer {
    max-width: 40%;
    display: inline-block;
    margin-bottom: 7vh;
}
.MovieName{
    text-align: left;
    margin-left: 265px;
}
.MovieProducers{
    text-align: left;
}
</style>
