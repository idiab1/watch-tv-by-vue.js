<template>
  <div class="home">
    <!-- Movie Card -->
    <div class="movie-card">
      <router-link to="/movie/tt234690">
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
        <form class="search-form" @submit.prevent="">
          <input type="text" placeholder="What are you looking for?" />
          <input type="submit" value="Search"/>
        </form>
      </div>
    </div>
    <!-- End of Search Box -->



  </div>
</template>

<script>
// @ is an alias to /src

export default {
  // name: "Home",
};
</script>

<style lang="scss">
.home{
  .movie-card{
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
      
      @media(max-width: 600px){
        width: 75%;
        display: block;
        margin: auto;
        margin-bottom: 25px;
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
      
    }
  }
}
/* End of Search box */



</style>