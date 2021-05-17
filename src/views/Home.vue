<template>
  <div class="home">
    <!-- Movie Card -->
    <div class="movie-banner">
      <router-link to="/movie/tt3896198">
        <img class="movie-image" src="../assets/images/naruto-wallpaper.jpg" alt="Naruto Poster"/>
        <div class="movie-details">
          <h2>Naruto</h2>
          <p>Naruto Uzumaki, a mischievous adolescent ninja, struggles as he searches for recognition and dreams of becoming the Hokage, the village's leader and strongest ninja.</p>
        </div>
      </router-link>
    </div>
    <!-- End of Movie Card -->

    <!-- Search Box -->
    <div class="search-box">
      <div class="container">
        <form class="search-form" @submit.prevent="SearchMovies()">
          <input type="text" placeholder="What are you looking for?" v-model="search" />
          <input type="submit" value="Search"/>
        </form>
      </div>
    </div>
    <!-- End of Search Box -->

    <!-- Movies List -->
    <div class="movies-section">
      <div class="container">
        <div class="movies-list">
          <div class="movie" v-for="movie in movies" :key="movie.imdbID">
            <router-link class="movie-link" :to="'/movie/' + movie.imdbID">
              <div class="movie-image">
                <img class="movie-poster" :src="movie.Poster" :alt="movie.Title"/>
                <div class="movie-type">
                  <span>{{movie.Type}}</span>
                </div>
              </div>
              <div class="movie-details">
                <p class="date">{{movie.Year}}</p>
                <h3>{{movie.Title}}</h3>
              </div>
            </router-link>
          </div>
        </div>
      </div>
    </div>
    <!-- End of Movies List -->


  </div>
</template>

<script>
// @ is an alias to /src
import { ref } from 'vue';
import env from '@/env.js';

export default {
  setup() {
    const search = ref("");
    const movies = ref([]);

    const SearchMovies = () =>{
      if (search.value != "") {
        fetch(`http://www.omdbapi.com/?i=tt3896198&apikey=${env.apikey}&s=${search.value}`)
        .then(response => response.json())
        .then(data => {
          movies.value = data.Search;
            search.value = "";
          // console.log(data);
        })
      }
    }

    return{
      search,
      movies,
      SearchMovies
    }

  }
};
</script>

<style lang="scss">
.home{
  .movie-banner{
    position: relative;
    .movie-image{
      position: relative;
      display: block;
      width: 100%;
      height: 350px;
      object-fit: cover;
      z-index: 0;
    }
    .movie-details{
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(0, 0, 0, 0.6);
      padding: 20px;
      z-index: 1;
      h2{
        color: #fff;
        margin-bottom: 15px;
      }
      p{
        color: #fff;
        line-height: 1.4;
        font-size: 18px;
      }
    }
  }
}

/* Search box */
.search-box{
  padding: 30px 0;
  text-align: center;
  .search-form{
    input[type="text"]{
      padding: 12px 10px;
      border: none;
      margin: 0 10px;
      width: 40%;
      font-size: 14px;
      text-transform: capitalize;
      &:focus{
        box-shadow: 0px 0px 6px rgb(0 0 0 / 82%);
        outline: none;
        border: none;
      }
      &::placeholder{
        color: #454545
      }
      // Media query for small screen
      @media(max-width: 599.9px){
        width: 75%;
        display: block;
        margin: auto;
        margin-bottom: 25px;
      }

      // Media query for medium screen
      @media(min-width: 600px) and (max-width: 899.9px){
        width: 60%;
      }

    }
    input[type="submit"]{
      padding: 14px 20px;
      border: none;
      background-color: #0cc69d;
      font-size: 14px;
      font-weight: 600;
      text-transform: capitalize;
      letter-spacing: 1px;
      line-height: 1;
      cursor: pointer;
      color: #fff;
    }
  }
}
/* End of Search box */

/* Movies Content*/
.movies-section{
  padding: 25px 0 40px;
  .movies-list{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;

    .movie{
      max-width: 30%;
      flex: 1 1 30%;
      margin: 12px;
      box-shadow: 0px 0px 3px 1px #595959;

      @media(max-width: 599.8px){
        max-width: 60%;
        flex: 0 0 60%;

      }
      @media(min-width: 600px) and (max-width: 899.9px){
        max-width: 45%;
        flex: 0 0 45%;

      }

      .movie-link{
        display: flex;
        flex-direction: column;
        height: 100%;
        .movie-image{
          position: relative;
          display: block;
          img{
            display: block;
            width: 100%;
            height: 275px;
          }
          .movie-type{
            position: absolute;
            padding: 8px 16px;
            right: 0;
            background-color: #0cc69d;
            bottom: 16px;
            span{
              text-transform: capitalize;
              color: #FFF;

            }
          }
        }
        .movie-details{
          background-color: #cecece;
          padding: 16px 8px;
          flex: 1 1 100%;
          .date{
            color: #3c3c3c;
            font-size: 15px;
          }
          h3{
            color: #000;
            font-size: 16px;
            margin-top: 5px;
            font-weight: 400;
          }
        }
      }
    }
  }
}

/* End of movies content */

</style>