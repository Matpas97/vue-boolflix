<template>
    <div class="card">
         <p>Title: {{movie.title}}</p> 
         <p>Original Title: {{movie.original_title}}</p> 
         <StarsRatingComponent :vote="movie.vote_average" />
         <p>Language: 
             <FlagComponent :language="movie.original_language"/>
         </p> 
         <PosterComponent :alt="movie.title" :image="movie.poster_path"/>
     </div>
 </template>
 
 <script>
 
 import FlagComponent from '@/components/FlagComponent.vue'
 import PosterComponent from '@/components/PosterComponent.vue'
 import StarsRatingComponent from '@/components/StarsRatingComponent.vue'
 export default {
     name: 'MovieCardComponent',
     props: {
         movie: Object
     },
     components: {
         FlagComponent,
         PosterComponent,
         StarsRatingComponent
     }
 }
 </script>
 
 <style lang="scss" scoped>
 .card{
   border: 1px solid #333;
 }
 
 </style>