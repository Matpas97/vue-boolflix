<template>
    <img class="poster" :src="imageUrl" :alt="alt" @error="setUnavailablePoster($event)">
  </template>
  
  <script>
  export default {
      name: 'PosterComponent',
      props: {
          image: String,
          width: Number,
          alt: String
      },
      computed:{
          imageUrl(){
  
              const width = this.width || 500;
  
              return 'https://image.tmdb.org/t/p/w' + width + this.image;
          },
      },
      methods: {
          setUnavailablePoster(event){
              event.target.src = 'https://www.metrorollerdoors.com.au/wp-content/uploads/2018/02/unavailable-image-300x225.jpg'
          }
      }
  }
  </script>
  
  <style lang="scss" scoped>
  .poster{
    object-fit: cover;
    width: 100%;
  }
  </style>