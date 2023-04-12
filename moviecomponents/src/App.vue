<template>
  <div>
    <h1 class="PageHeading">Movie Information</h1>
    <MovieBox v-for="(movieData, index) in listMovie" :key="index" :movieData="movieData" />
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
      movieDataList: [],
      listMovie: [155, 550, 286217, 152603]
    }
  },
  mounted () {
    Promise.all(this.listMovie.map(movieId => axios.get(`https://api.themoviedb.org/3/movie/${movieId}?api_key=c6daa157a2252e0b4426c4bf32d06641`)))
      .then((responses) => {
        this.listMovie = responses.map(response => response.data)
        console.log(this.listMovie)
      })
      .catch((error) => {
        console.log(error)
      })
  }
})
</script>
<style>
body{
  text-align: left;
  border: 0px;
  padding: 0px;
  background: #1E1E1E;
  color: beige;
  font-family: 'Helvetica Neue Light', 'HelveticaNeue-Light', 'Helvetica Neue', sans-serif;
}

@media (min-width: 1025px) {
  body{
    margin-left: 30%;
    margin-right: 30%;
    max-width: auto;
  }
}
@media (max-width: 1024px) and (min-width: 512px){
  body{
    margin-left: 15%;
    margin-right: 15%;
    width: auto;
  }
}
.PageHeading{
  text-align: center;
}
</style>
