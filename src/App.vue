<template>
  <div>
    <!-- Navbar -->
    <AppNavbar/>
    <!-- End of Navbar -->

    <!-- Main -->
    <main class="main-content">
      <router-view />
    </main>
    <!-- Footer -->
    <AppFooter />
    <!-- End of footer -->
  </div>
</template>

<script>
import AppFooter from "@/components/app-footer.vue";
import AppNavbar from "@/components/app-navbar.vue";

export default {
  components: {
    AppNavbar,
    AppFooter,
  },
};
</script>

<style lang="scss">
/* Global rules */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}

body {
  background-color: #393e46;
}

a {
  text-decoration: none;
}

.container {
  max-width: 1120px;
  margin: auto;
}

// 219897
// 42b983
/* End of Global rules */

// #app {
//   font-family: Avenir, Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
// }

.navbar {
  padding: 30px;
  background-color: #222831;
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
