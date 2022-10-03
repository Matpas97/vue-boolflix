<template>
    <div class="card">
     <div class="posterComponent">
        <PosterComponent :alt="title" :image="image"/>
     </div>   
     <div class="info">
         <p>Title: {{title}}</p> 
         <p>Original Title: {{originalTitle}}</p> 
         <StarsRatingComponent :vote="vote" />
         <p class="long-text">{{overview}}</p>
         <p>Language:<FlagComponent :language="language"/></p> 
        
      </div>
        
     </div>
 </template>
 
 <script>
 
 import FlagComponent from '@/components/FlagComponent.vue'
 import PosterComponent from '@/components/PosterComponent.vue'
 import StarsRatingComponent from '@/components/StarsRatingComponent.vue'
 export default {
     name: 'CardComponent',
     props: {
        title: String,
        originalTitle: String,
        vote: Number,
        language: String,
        image: String,
        overview: String
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
   position: relative;
   .posterComponent{
     position: absolute;
     top: 0;
     left: 0;
   }
   &:hover .posterComponent{
        display: none;
   }
   height: 400px;
   .long-text{
     max-height: 150px;
     overflow-y: auto;
   }
 }
 
 
 </style>