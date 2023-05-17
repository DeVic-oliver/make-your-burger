<template>
  <header>
    <div class="container">
      <div>
        <RouterLink to="/">
          <img alt="Burger Logo" class="logo" src="/img/logo.png" width="125" height="125" />
        </RouterLink>
      </div>
      <div class="wrapper">
        <nav>
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/pedidos">Pedidos</RouterLink>
        </nav>
      </div>
    </div>
  </header>
</template>

<script>
    export default {
        name: "Navbar"
    }
</script>

<style scoped>
  header{
    background-color: #222;
  }

  .container{
    align-items: center;
    display: grid;
    grid-template-columns: 1fr 1fr;
  }

  .wrapper{
    text-align: center;
  }

  .wrapper nav{
    display: flex;
    justify-content: space-around;
    margin: 0 auto;
    max-width: 150px;
    text-transform: uppercase;
    width: 100%;
  }

  .wrapper nav > *:hover{
    color: #fff;
  }

</style>