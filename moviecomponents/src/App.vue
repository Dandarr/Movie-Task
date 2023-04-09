<template>
  <div>
    <h1>Movie Information</h1>
    <MovieBox :movieData="movieData" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import MovieBox from './components/MovieComponent.vue'
import axios from 'axios'

export default defineComponent({
  name: 'App',
  components: {
    MovieBox
  },
  data () {
    return {
      movieData: {} as Record<string, unknown>,
      listMovie: []
    }
  },
  mounted () {
    axios.get('https://api.themoviedb.org/3/movie/550?api_key=c6daa157a2252e0b4426c4bf32d06641')
      .then((response) => {
        this.movieData = response.data
        this.listMovie = response.data
        console.log(this.movieData, this.listMovie)
      })
      .catch((error) => {
        console.log(error)
      })
  }
})
</script>
