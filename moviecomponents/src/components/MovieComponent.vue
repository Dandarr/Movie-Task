<template>
    <div>
        <h1>{{ movieData.title }}</h1>
        <img :src="'https://image.tmdb.org/t/p/w500' + movieData.poster_path" :alt="movieData.title + ' poster'">
        <p><strong>Release Date:</strong> {{ movieData.release_date }}</p>
        <p><strong>Runtime:</strong> {{ movieData.runtime }} minutes</p>
        <p><strong>Genres:</strong> {{ getGenres(movieData.genres) }}</p>
        <p><strong>Overview:</strong> {{ movieData.overview }}</p>
        <p><strong>Production Companies:</strong></p>
        <ul>
            <li v-for="company in movieData.production_companies" :key="company.id">
                {{ company.name }}
            </li>
        </ul>
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
    getGenres (genres) {
      return genres.map(genre => genre.name).join(', ')
    }
  }
}
</script>

<style>
/* Add styles as desired */
</style>
