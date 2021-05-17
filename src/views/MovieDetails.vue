<template>
  <div class="movie-details">
    <div class="container">
      <div class="movie-content">
        <div class="poster">
          <img class="movie-poster" :src="movie.Poster" :alt="movie.Title"/>
        </div>
        <div class="content">
          <div class="movie-head">
            <h2 class="movie-title"> {{movie.Title}}</h2>
            <span class="movie-date">
              {{movie.Year}}
            </span>
          </div>
          <div class="movie-description">
            <p>{{movie.Plot}}</p>
          </div>

        </div>
        

      </div>
    </div>
  </div>
</template>

<script>
import {ref, onBeforeMount} from "vue";
import {useRoute} from "vue-router";
import env from '@/env.js';

export default {
  setup() {
    const movie = ref({});
    const route = useRoute();
    
    onBeforeMount(() => {
      
      fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
        .then(response => response.json())
        .then(data => {
          movie.value = data;
        });


    });

    return{
      movie
    }

  }
}
</script>

<style lang="scss">
.movie-details{
    padding: 40px 0;
  .movie-content{
    width: 80%;
    margin: auto;
    display:flex;
    flex-direction: row;
    background-color: #cecece;
    .poster{
      width: 40%;
      img{
        width: 100%;
        height: 100%
      }
    }
    
    .content{
      width: 60%;
      padding: 20px;
      .movie-head{

        .movie-title{
          margin-bottom: 7px;
          color: #484848;
        }
        .movie-date{
          background-color: #0cc69d;
          padding: 5px;
          font-size: 16px;
          color: #242424;
        }
      }

      .movie-description{
        margin: 15px 0;
        p{
          font-size: 17px;
          line-height: 1.4;
          font-weight: 400;
          color: #3b3b3b;
        }
      }

    }

    
    
  }

  }
</style>