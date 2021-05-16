<template>
  <div>
    <nav class="navbar">
      <div class="container">
        <div class="navbar-logo">
          <router-link to="/">Home</router-link>
        </div>
      </div>
    </nav>
  </div>
</template>


<style lang="scss">
.navbar{
  padding: 20px;
  background-color: #222831;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0px 0px 3px rgb(255 255 255 / 22%);
  .navbar-logo {
    a {
      font-weight: bold;
      color: #42b983;
      // &.router-link-exact-active {
      //   color: #42b983;
      // }
    }
  }
}
</style>