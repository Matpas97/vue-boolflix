<template>
  <div id="app">
    <HeaderComponent @search="queryApi" />

    <div class="container">
      <h2>Movies</h2>
      <!--MovieCardComponent v-for="movie in movies" :key="movie.id" :movie="movie"  /-->
      <div class="card-container">
        <CardComponent  v-for="movie in movies" :key="movie.id"
          :title="movie.title"
          :originalTitle="movie.original_title"
          :vote="movie.vote_average"
          :language="movie.original_language"
          :image="movie.poster_path"
            :overview="movie.overview"
        />
      </div>

      <h2>TV Series</h2>
      <!--TvSerieCardComponent v-for="tvSerie in tvSeries" :key="tvSerie.id" :tv="tvSerie"  /-->
      <div class="card-container">
        <CardComponent v-for="tvSerie in tvSeries" :key="tvSerie.id"
          :title="tvSerie.name"
          :originalTitle="tvSerie.original_name"
          :vote="tvSerie.vote_average"
          :language="tvSerie.original_language"
          :image="tvSerie.poster_path"
          :overview="tvSerie.overview"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import { apiKey } from '@/env'

import HeaderComponent from '@/components/HeaderComponent'

//import MovieCardComponent from '@/components/MovieCardComponent.vue'
//import TvSerieCardComponent from '@/components/TvSerieCardComponent.vue'
import CardComponent from '@/components/CardComponent.vue'

export default {
  name: 'App',
  data(){
    return {
      query: '',
      movies: [],
      tvSeries: [],
      apiUrl: 'https://api.themoviedb.org/3/'
    }
  },
  methods:{
    queryApi(textToSearch){
      const params = `?api_key=${apiKey}&query=${textToSearch}&language=it-IT`

      axios.get(`${this.apiUrl}search/movie${params}`)
        .then((response)=>{
          this.movies = this.getDataFromApiResponse(response);  
        })
        .catch(error=> {
          console.log(error.message)
        });
      axios.get(`${this.apiUrl}search/tv${params}`)
        .then((response)=>{
           this.tvSeries = this.getDataFromApiResponse(response);  
        })
        .catch(error=> {
          console.log(error.message)
        });
    },
    getDataFromApiResponse(response){
      console.log(response);
      return response.status === 200? response.data.results : []    
    }
  },
  components:{
    HeaderComponent,
 //   MovieCardComponent,
 //   TvSerieCardComponent,
    CardComponent
  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap';
body{
  background-color: #ddd;
}
.card-container{
  display: flex;
  flex-wrap: nowrap;
  overflow-x: auto;
  > * {
    width: 25%;
    flex-shrink: 0;
  }
}
</style>
