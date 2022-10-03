<template>
    <div class="card">
       <p>Title: {{tv.name}}</p> 
       <p>Original Title: {{tv.original_name}}</p> 
       <StarsRatingComponent :vote="tv.vote_average" />
       <p>Language: 
         <FlagComponent :language="tv.original_language"/>
       </p> 
       <PosterComponent :image="tv.poster_path" :width="500" :alt="tv.name" />
   </div>
</template>

<script>
import FlagComponent from '@/components/FlagComponent.vue'
import PosterComponent from '@/components/PosterComponent.vue'
import StarsRatingComponent from '@/components/StarsRatingComponent.vue'
export default {
   name: 'TvSerieCardComponent',
   props: {
       tv: Object
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