<template>
  <div>
    <footer class="footer">
      <div class="container">
        <div class="footer-content">
          <p>&copy; Copyright all reserved 2021 coding by <a href="#">Islam Diab</a></p>
        </div>
      </div>
    </footer>
  </div>
</template>

<style lang="scss">
.footer {
  padding: 20px;
  background-color: #222831;
  display: flex;
  justify-content: center;
  align-items: center;
  .footer-content{
    p{
      color: #fff;
      font-size: 17px;
      letter-spacing: 1px;
      text-transform: capitalize;
      font-weight: 300;
      a {
        font-weight: bold;
        color: #42b983;
        
      }
    }
  }
}
</style>
